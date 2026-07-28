
# Network Configuration

## Overview

The network infrastructure for this lab was designed to simulate a small business environment using VMware Workstation. The environment consists of an isolated internal network for domain services and a separate NAT network for internet connectivity.

This design allows Windows Server services such as Active Directory, DNS, DHCP, and File Sharing to operate independently while still providing internet access for updates and software installation.

---

# Network Topology

The lab uses two virtual networks.

| Network | VMware Network | Purpose |
|---------|----------------|---------|
| Internal LAN | VMnet2 | Active Directory, DNS, DHCP, File Sharing |
| External Network | VMnet8 (NAT) | Internet access and software updates |

Each virtual machine has two network adapters:

- **Ethernet1** – Internal enterprise network (VMnet2)
- **Ethernet0** – VMware NAT network (VMnet8)

---

# IP Addressing Scheme

## Servers

| Device | Role | IP Address |
|---------|------|------------|
| DC01 | Domain Controller, DNS, DHCP | 10.10.1.10 |
| FS01 | File Server | 10.10.1.20 |

---

## DHCP Scope

The DHCP service was configured on DC01.

| Setting | Value |
|---------|-------|
| Network | 10.10.1.0/24 |
| Scope Range | 10.10.1.100 – 10.10.1.200 |
| Subnet Mask | 255.255.255.0 |
| DNS Server | 10.10.1.10 |
| DNS Domain | kabtech.local |

Client computers automatically receive IP addresses from this scope.

---

# VMware Network Configuration

The lab uses two VMware virtual adapters.

## VMnet2

Purpose:

- Active Directory traffic
- DNS
- DHCP
- SMB File Sharing
- Group Policy
- Domain authentication

This network is isolated from the internet.

---

## VMnet8 (NAT)

Purpose:

- Windows Updates
- Internet access
- Software downloads

This adapter is not used for domain communication.

---

# DNS Configuration

DNS is hosted on the Domain Controller (DC01).

The **kabtech.local** forward lookup zone was created and integrated with Active Directory.

Static A records were created for infrastructure servers.

| Host | IP Address |
|------|------------|
| dc01 | 10.10.1.10 |
| fs01 | 10.10.1.20 |

The DHCP server was configured to distribute:

- DNS Server: **10.10.1.10**
- DNS Suffix: **kabtech.local**

---

# DHCP Configuration

The DHCP role was installed and authorized on DC01.

The following options were configured:

| Option | Value |
|---------|-------|
| Scope | 10.10.1.0/24 |
| Address Pool | 10.10.1.100 – 10.10.1.200 |
| DNS Server | 10.10.1.10 |
| DNS Domain | kabtech.local |
| Lease Duration | 8 Days |

After renewing their leases, client computers automatically received the correct IP configuration.

---

# Client Network Configuration

All Windows client computers were configured with:

- DHCP enabled
- Automatic DNS configuration
- Automatic IP addressing
- Domain membership (kabtech.local)

The clients successfully received:

- IP Address
- DNS Server
- DNS Suffix
- DHCP Lease

from the Windows DHCP server.

---

# Network Validation

The following connectivity tests were completed.

## DHCP Verification

The following commands were used:

```powershell
ipconfig /release
ipconfig /renew
ipconfig /all
```

Result:

- DHCP leases were successfully assigned.
- Clients received addresses within the configured DHCP scope.
- DNS settings were automatically applied.

---

## DNS Verification

The following commands were executed:

```powershell
nslookup dc01.kabtech.local
ping dc01.kabtech.local
```

Result:

- DNS successfully resolved domain resources.
- Hostnames resolved to the correct IP addresses.
- Clients communicated with the Domain Controller without issues.

---

## Domain Connectivity

Connectivity to Active Directory was verified using:

```powershell
ping 10.10.1.10
ping dc01.kabtech.local
```

Successful responses confirmed proper communication between clients and the Domain Controller.

---

# Network Challenges and Resolution

Several networking issues were encountered during deployment.

## Issue 1 – Incorrect DHCP Server

Initially, client computers obtained IP addresses from VMware's DHCP service instead of the Windows DHCP server.

### Cause

Virtual machines were connected to the wrong VMware virtual network.

### Resolution

- Created an isolated VMnet2 network.
- Connected all enterprise virtual machines to VMnet2.
- Renewed DHCP leases.

Clients then received addresses from the Windows DHCP server.

---

## Issue 2 – Incorrect DNS Server

Some clients initially used the VMware NAT DNS server instead of the internal DNS server.

### Cause

The DHCP scope was distributing an incorrect DNS server address.

### Resolution

Updated DHCP Option 006 to advertise the Domain Controller (10.10.1.10) as the DNS server and renewed client leases.

---

## Issue 3 – Duplicate DNS Records

The DNS zone contained multiple A records for the Domain Controller, including an obsolete address from the NAT network.

### Cause

The Domain Controller had dynamically registered both its internal and external IP addresses.

### Resolution

The incorrect DNS record was removed, leaving only the internal enterprise IP address.

This ensured reliable name resolution for all domain clients.

---

# Final Network Status

At the completion of the configuration:

- All client computers obtained IP addresses from the Windows DHCP server.
- DNS resolution functioned correctly.
- Clients successfully joined the kabtech.local domain.
- Active Directory communication operated normally.
- Internal services used the isolated enterprise network.
- Internet access remained available through the NAT adapter.

The network configuration provides a stable foundation for centralized Windows Server administration and enterprise client management.
