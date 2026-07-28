

# Project Overview

## Project Background

KabTech is a fictional small-to-medium business used to simulate a real-world enterprise IT environment. As the company expanded, managing users, computers, network resources, and security through individual workstations became inefficient and difficult to maintain.

To improve operational efficiency, KabTech decided to deploy a centralized Windows Server 2022 infrastructure using Microsoft Active Directory technologies. This project documents the planning, deployment, configuration, and management of that environment.

The lab was built using VMware Workstation to simulate an enterprise network and demonstrate practical Windows Server administration skills commonly required in IT Support and Systems Administration roles.

---

# Business Scenario

KabTech has multiple departments, including:

- Human Resources (HR)
- Finance
- Information Technology (IT)
- Sales
- Management

Each department requires secure access to shared resources while maintaining appropriate separation between users and data.

Employees also need:

- Centralized user authentication
- Department-specific shared folders
- Automatic network drive mapping
- Consistent security policies
- Reliable name resolution
- Automatic IP address assignment
- Centralized workstation administration

To meet these requirements, a Windows Server 2022 domain environment was deployed.

---

# Project Objectives

The primary objectives of this project were to:

- Deploy Windows Server 2022 as the central management server.
- Configure Active Directory Domain Services (AD DS).
- Implement DNS and DHCP services.
- Design a structured Organizational Unit (OU) hierarchy.
- Create departmental users, groups, and computer accounts.
- Configure enterprise file sharing with appropriate permissions.
- Deploy Group Policy Objects (GPOs) for centralized management.
- Join Windows client computers to the domain.
- Manage systems using Windows Admin Center.
- Monitor server health and performance using built-in Windows tools.

---

# Scope of the Project

The project includes the deployment and configuration of:

- Windows Server 2022
- Active Directory Domain Services
- DNS Server
- DHCP Server
- Enterprise Organizational Units
- User and Group Management
- Departmental File Shares
- NTFS and Share Permissions
- Group Policy Objects
- Windows Admin Center
- Performance Monitoring
- Reliability Monitoring
- Domain-Joined Windows Client Computers

The project does not include cloud services, Microsoft 365, Azure Active Directory, or third-party monitoring solutions.

---

# Lab Environment

The lab consists of one virtual enterprise network hosted in VMware Workstation.

### Servers

| Server  | Role 
|---------|--------------------------------------------
| DC01    | Domain Controller, DNS Server, DHCP Server 
| FS01    | File Server 

### Client Computers

| Computer | Purpose 
|----------|--------------------------------
| PC01     | Domain-joined workstation 
| PC02     | Domain-joined workstation 
| PC03     | Domain-joined workstation 

---

# Technologies Used

| Technology                       | Purpose 
|----------------------------------|---------
| Windows Server 2022              | Server operating system 
| Windows 11                       | Client operating system 
| VMware Workstation               | Virtualization platform 
| Active Directory Domain Services | Identity and access management 
| DNS                              | Name resolution 
| DHCP                             | Automatic IP address assignment 
| Group Policy                     | Centralized configuration management 
| SMB                              | Network file sharing 
| Windows Admin Center             | Remote administration 
| Performance Monitor              | Performance monitoring 
| Reliability Monitor              | System reliability monitoring 

---

# Expected Outcomes

At the completion of this project, the enterprise environment provides:

- Centralized user authentication.
- Centralized computer management.
- Automatic IP address assignment.
- Reliable DNS name resolution.
- Department-based access control.
- Secure shared folders.
- Automatic drive mapping.
- Standardized workstation configuration through Group Policy.
- Centralized administration using Windows Admin Center.
- Improved visibility into server performance and system reliability.

---

# Project Summary

This Windows Server 2022 Enterprise IT Lab demonstrates the deployment and administration of a complete on-premises Windows domain infrastructure. The project reflects many of the core responsibilities performed by IT Support Specialists and Systems Administrators, including server deployment, Active Directory management, network services configuration, file services administration, Group Policy management, and ongoing system monitoring.
