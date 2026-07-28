# Windows_Server-2022-Enterprise-IT-Lab
Enterprise Windows Server 2022 homelab featuring Active Directory, DNS, DHCP, File Services, Group Policy, Windows Admin Centre, and enterprise workstation management using VMware Workstation.



# Windows Server 2022 Enterprise IT Lab

## Overview

This repository documents the design, deployment, and administration of a Windows Server 2022 enterprise lab built using VMware Workstation. The lab simulates the IT infrastructure of a small business and demonstrates the deployment and management of core Windows Server services, including Active Directory, DNS, DHCP, File Services, Group Policy, and Windows Admin Center.

The project was designed to strengthen practical skills in Windows Server administration, enterprise networking, user and computer management, centralized policy deployment, file sharing, and system monitoring. It also serves as a portfolio project showcasing hands-on experience with enterprise IT infrastructure.

---

## Project Objectives

This lab was built to:

- Deploy a Windows Server 2022 domain environment
- Configure Active Directory Domain Services (AD DS)
- Implement DNS and DHCP services
- Design an organized Active Directory OU structure
- Create and manage users, groups, and computers
- Configure departmental shared folders with NTFS and Share permissions
- Deploy Group Policy Objects (GPOs)
- Join Windows clients to the domain
- Manage systems using Windows Admin Center
- Monitor server performance and system health
- Practice enterprise troubleshooting and administration

---

## Lab Environment

| Component               | Details 
|-----------              |---------------------------------------------------------------------
| Hypervisor              | VMware Workstation 
| Server Operating System | Windows Server 2022 Standard (Desktop Experience) 
| Client Operating System | Windows 11 
| Domain Name             | kabtech.local 
| Domain Controller       | DC01 
| File Server             | FS01 
| Client Computers        | PC01, PC02, PC03 
| Directory Service       | Active Directory Domain Services 
| DNS                     | Microsoft DNS Server 
| DHCP                    | Microsoft DHCP Server 
| File Sharing            | SMB 
| Remote Management       | Windows Admin Center 

---

## Infrastructure

The environment consists of:

- **DC01** – Domain Controller, DNS Server and DHCP Server
- **FS01** – Enterprise File Server hosting departmental shared folders
- **PC01** – Domain-joined client workstation
- **PC02** – Domain-joined client workstation
- **PC03** – Domain-joined client workstation

---

## Core Technologies

- Windows Server 2022
- Active Directory Domain Services (AD DS)
- DNS Server
- DHCP Server
- Group Policy Management
- NTFS Permissions
- SMB File Sharing
- Windows Admin Center
- Performance Monitor
- Reliability Monitor
- VMware Virtual Networking

---

## Skills Demonstrated

- Windows Server Administration
- Active Directory Administration
- DNS Configuration and Troubleshooting
- DHCP Configuration
- Group Policy Management
- Enterprise File Server Administration
- NTFS and Share Permissions
- User and Group Administration
- Domain Management
- Enterprise Troubleshooting
- Windows Admin Center Administration
- System Monitoring
- VMware Networking

---

## Documentation

The project documentation is organized into the following sections:

| Document              | Description 
|-----------------------|-------------------------------------------------------------
| Project Overview      | Business scenario and project goals 
| Lab Architecture      | Infrastructure and network design 
| Network Configuration | IP addressing, DNS, and DHCP configuration 
| Active Directory      | Domain structure, users, groups, and Organizational Units 
| File Server           | Shared folders, permissions, and drive mapping 
| Group Policy          | Enterprise policy configuration 
| Windows Admin Center  | Remote server and workstation management 
| System Monitoring     | Performance and reliability monitoring 
| Troubleshooting       | Common issues encountered and resolutions 
| Lessons Learned       | Key takeaways and future improvements 

---

## Screenshots

The **images** folder contains screenshots of:

- Active Directory structure
- DNS configuration
- DHCP scope
- Shared folders
- Group Policy Objects
- Windows Admin Center
- Performance Monitor
- Reliability Monitor
- Domain-joined clients
- Enterprise file shares

---

## Project Status

**Current Status:** Completed

The lab includes:

- Active Directory Domain Services
- DNS Server
- DHCP Server
- Enterprise Organizational Unit structure
- Departmental users and security groups
- Domain-joined Windows clients
- Enterprise file server
- Departmental network shares
- Group Policy deployment
- Windows Admin Center
- Performance monitoring
- Reliability monitoring

---

## Author

**Mohamed Kabia**

Bachelor of Science (Honours) in Information Technology

Aspiring Windows Server Administrator | IT Support Specialist | Systems Administrator
