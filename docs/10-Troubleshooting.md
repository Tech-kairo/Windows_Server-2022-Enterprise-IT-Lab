docs/10-Troubleshooting.md

# Troubleshooting

## Overview

Throughout the Windows Server 2022 Enterprise IT Lab, several technical challenges were encountered and resolved. This section documents the troubleshooting process, including the symptoms, root causes, corrective actions, and final outcomes.

Documenting troubleshooting steps demonstrates practical problem-solving skills and provides a useful reference for future deployments.

---

# Troubleshooting Summary

| Issue | Status |
|--------|--------|
| DHCP clients receiving incorrect IP addresses | Resolved |
| VMware network adapter configuration | Resolved |
| DNS server assigned incorrectly by DHCP | Resolved |
| Duplicate DNS records for DC01 | Resolved |
| Client DNS resolution failures | Resolved |
| Windows Admin Center connectivity | Resolved |
| Network drive mapping not appearing | Resolved |
| Sysmon XML configuration error | Identified |

---

# Issue 1 – DHCP Clients Receiving Incorrect IP Addresses

## Problem

Client computers received IP addresses from the VMware NAT network instead of the internal corporate network.

Example:

```
192.168.100.x
```

instead of

```
10.10.1.x
```

## Root Cause

The virtual machines were connected to the wrong VMware virtual network (VMnet).

## Resolution

- Created a dedicated internal VMnet.
- Connected DC01, FS01, and client computers to the same internal network.
- Renewed DHCP leases using:

```powershell
ipconfig /release
ipconfig /renew
```

## Result

Clients successfully received addresses from the corporate DHCP scope.

Example:

```
10.10.1.100
10.10.1.101
10.10.1.102
```

---

# Issue 2 – Incorrect DNS Server Assigned by DHCP

## Problem

Clients received the wrong DNS server through DHCP.

Example:

```
192.168.100.138
```

instead of

```
10.10.1.10
```

## Root Cause

The DHCP Scope Option for DNS Servers (Option 006) pointed to the incorrect address.

## Resolution

Updated DHCP Scope Option 006 to use:

```
10.10.1.10
```

Renewed client DHCP leases.

## Result

Clients received the correct DNS server and domain name resolution worked properly.

---

# Issue 3 – Duplicate DNS Records

## Problem

DNS returned two IP addresses for the domain controller.

Example:

```
10.10.1.10
192.168.100.138
```

## Root Cause

The domain controller had registered both its internal and external network interfaces in DNS.

## Resolution

Disabled DNS registration on the external adapter and removed the incorrect DNS record from the `kabtech.local` zone.

## Result

DNS now resolves the domain controller to the correct internal IP address only.

---

# Issue 4 – DNS Resolution Failure

## Problem

Client computers could ping the domain controller by IP address but failed to resolve hostnames using `nslookup`.

## Root Cause

Some clients were using the wrong DNS server due to adapter configuration or DHCP settings.

## Resolution

Verified the DNS server on client computers, renewed DHCP leases, and ensured the internal adapter used the domain controller (`10.10.1.10`) as its DNS server.

## Result

Hostname resolution was restored successfully.

---

# Issue 5 – Windows Admin Center Connection Issues

## Problem

Managed computers could not initially be opened from Windows Admin Center.

## Root Cause

Remote management prerequisites and trust configuration required additional setup.

## Resolution

Verified:

- WinRM configuration
- Windows Firewall rules
- PowerShell Remoting
- Domain credentials
- Computer connectivity

Re-added the managed devices using the correct credentials.

## Result

Successfully connected to:

- DC01
- FS01
- PC01
- PC02

through Windows Admin Center.

---

# Issue 6 – Network Drive Mapping

## Problem

A newly created HR user did not receive the mapped HR network drive after logging in.

## Root Cause

The user had not yet received the updated Group Policy configuration.

## Resolution

Forced a Group Policy update using:

```powershell
gpupdate /force
```

Logged off and back on to refresh user policies.

## Result

The HR network drive appeared automatically in File Explorer.

---

# Issue 7 – Sysmon Configuration

## Problem

Sysmon installation failed because the configuration file could not be parsed.

## Root Cause

An HTML page was downloaded instead of the actual XML configuration file.

## Resolution

Verified that the downloaded file was an HTML document rather than a valid XML configuration. Since Sysmon was not required for the objectives of this IT Support lab, installation was not completed.

## Result

The issue was identified and documented, but Sysmon was intentionally excluded from the final lab.

---

# Troubleshooting Methodology

The following approach was used to resolve issues throughout the project:

1. Identify the problem.
2. Gather diagnostic information.
3. Determine the root cause.
4. Apply corrective actions.
5. Validate the solution.
6. Document the outcome.

---

# Key Commands Used

| Command | Purpose |
|---------|---------|
| `ipconfig /all` | View network configuration |
| `ipconfig /release` | Release DHCP lease |
| `ipconfig /renew` | Obtain a new DHCP lease |
| `ping` | Test network connectivity |
| `nslookup` | Verify DNS resolution |
| `gpupdate /force` | Refresh Group Policy |
| `gpresult /r` | Verify applied policies |
| `Get-DhcpServerv4Scope` | Verify DHCP scope |
| `Get-DhcpServerv4Lease` | View DHCP leases |

---

# Lessons Learned

This project reinforced several important IT administration concepts:

- Proper network segmentation is essential for reliable communication.
- Correct DNS configuration is critical for Active Directory functionality.
- DHCP scope options must be carefully configured.
- Group Policy changes often require a policy refresh or user sign-out.
- Windows Admin Center simplifies remote administration but depends on proper WinRM and firewall configuration.
- Systematic troubleshooting and documentation are valuable skills for IT support professionals.

---

# Summary

The troubleshooting activities completed during this lab strengthened practical Windows Server administration skills. Each issue was investigated, resolved where appropriate, and documented, demonstrating a structured approach to diagnosing and correcting common enterprise IT problems.


