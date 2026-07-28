
# Lab Architecture

## Overview

The Windows Server 2022 Enterprise IT Lab was designed to simulate the infrastructure of a small business environment. The architecture provides centralized identity management, automated network services, secure file sharing, and centralized administration using Microsoft Windows Server technologies.

The environment was deployed using VMware Workstation, allowing multiple virtual machines to communicate over an isolated virtual network while simulating a production enterprise environment.

---

# Infrastructure Overview

The lab consists of two Windows Server 2022 virtual machines and three Windows 11 client computers.

| Computer | Operating System | Primary Role |
|----------|------------------|--------------|
| DC01 | Windows Server 2022 | Domain Controller, DNS Server, DHCP Server |
| FS01 | Windows Server 2022 | File Server |
| PC01 | Windows 11 | Domain Client |
| PC02 | Windows 11 | Domain Client |
| PC03 | Windows 11 | Domain Client |

Each client computer is joined to the **kabtech.local** Active Directory domain and receives centralized management through Active Directory and Group Policy.

---

# Domain Architecture

The environment uses a single Active Directory forest and a single domain.

| Component | Value |
|----------|-------|
| Forest | kabtech.local |
| Domain | kabtech.local |
| Domain Controller | DC01 |
| DNS Zone | kabtech.local |

This design is suitable for small and medium-sized organizations by providing centralized authentication, authorization, and resource management.

---

# Network Architecture

The lab uses two virtual networks.

### Internal Enterprise Network

| Setting | Value |
|---------|-------|
| Network | VMnet2 |
| Subnet | 10.10.1.0/24 |
| Domain Controller | 10.10.1.10 |
| File Server | 10.10.1.20 |
| DHCP Scope | 10.10.1.100 – 10.10.1.200 |

The internal network is used for:

- Active Directory communication
- DNS queries
- DHCP services
- File sharing
- Domain authentication
- Group Policy processing

---

### External Network

The second network adapter connects virtual machines to the VMware NAT network.

This adapter provides:

- Internet access
- Windows Updates
- Software downloads
- Remote administration tools

The production services remain isolated on the internal enterprise network.

---

# Server Roles

## DC01

DC01 performs several critical infrastructure roles.

### Active Directory Domain Services

Provides:

- User authentication
- Computer authentication
- Security groups
- Organizational Units
- Group Policy processing

### DNS Server

Responsible for:

- Hostname resolution
- Domain service records
- Active Directory integration

### DHCP Server

Provides automatic IP configuration including:

- IP address assignment
- DNS server information
- DNS suffix
- Lease management

---

## FS01

FS01 is dedicated to enterprise file storage.

Shared folders include:

- HR
- Finance
- IT
- Public
- Software

Access is controlled using:

- NTFS Permissions
- SMB Share Permissions
- Active Directory Security Groups

---

# Active Directory Design

The Active Directory structure separates users and computers into Organizational Units (OUs) for easier administration and policy management.

The structure includes:

- Departments
  - HR
  - Finance
  - IT
  - Sales
  - Management
- Computers
  - Workstations
  - Servers
- Groups

This design allows Group Policies and permissions to be applied to specific departments without affecting the rest of the organization.

---

# Client Management

Each Windows client is configured to:

- Receive an IP address from DHCP
- Use the Domain Controller for DNS
- Join the kabtech.local domain
- Receive Group Policy settings
- Access departmental network drives
- Authenticate using Active Directory accounts

---

# Administrative Tools

The following management tools are used throughout the project.

| Tool | Purpose |
|------|---------|
| Server Manager | Server administration |
| Active Directory Users and Computers | User and OU management |
| DNS Manager | DNS administration |
| DHCP Manager | DHCP administration |
| Group Policy Management | Policy deployment |
| File Explorer | Share management |
| Windows Admin Center | Remote administration |
| Performance Monitor | Performance monitoring |
| Reliability Monitor | Reliability analysis |

---

# Security Design

The environment follows several security best practices.

These include:

- Centralized authentication through Active Directory
- Role-based access using security groups
- Department-specific file permissions
- Least privilege access
- Centralized policy management
- Automatic workstation configuration through Group Policy

---

# Scalability

Although designed for a small business, the infrastructure can easily be expanded by adding:

- Additional Domain Controllers
- Print Servers
- Application Servers
- Backup Servers
- Additional client computers
- New departments and Organizational Units

The Active Directory structure was designed to support future growth without requiring major architectural changes.

---

# Architecture Summary

The Windows Server 2022 Enterprise IT Lab provides a realistic enterprise infrastructure that demonstrates many of the core technologies used in business environments. By combining Active Directory, DNS, DHCP, File Services, Group Policy, and Windows Admin Center, the lab showcases the deployment and management of a centralized Windows domain while following industry-standard administrative practices.
