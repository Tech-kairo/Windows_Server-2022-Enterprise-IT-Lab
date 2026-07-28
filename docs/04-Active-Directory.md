
# Active Directory

## Overview

Active Directory Domain Services (AD DS) serves as the central identity and access management solution for the Windows Server 2022 Enterprise IT Lab. It provides centralized authentication, authorization, user management, computer management, and Group Policy administration across the domain.

The lab uses a single Active Directory forest and a single domain, allowing all users and computers to be managed from a central location.

---

# Domain Information

| Setting | Value |
|---------|-------|
| Forest | kabtech.local |
| Domain | kabtech.local |
| Domain Controller | DC01 |
| Functional Level | Windows Server 2022 |
| Authentication | Active Directory Domain Services |

---

# Organizational Unit (OU) Structure

The Active Directory environment is organized into Organizational Units (OUs) to simplify administration and allow Group Policies to be applied to specific users and computers.

The structure implemented in this lab is shown below.

```text
kabtech.local
│
├── Departments
│   ├── Finance
│   ├── HR
│   ├── IT
│   ├── Management
│   └── Sales
│
├── Computers
│   ├── Workstations
│   └── Servers
│
└── Groups
```

This design separates users, computers, and security groups into logical containers, making the environment easier to manage and expand.

---

# Departmental Organizational Units

Each department has its own Organizational Unit.

| OU | Purpose |
|----|---------|
| HR | Human Resources users |
| Finance | Finance users |
| IT | IT staff |
| Sales | Sales staff |
| Management | Management users |

This structure allows department-specific Group Policies and delegated administration.

---

# Computer Organizational Units

Computer accounts are separated from user accounts.

## Workstations

Contains all Windows 11 client computers.

Examples:

- PC01
- PC02
- PC03

---

## Servers

Contains enterprise servers.

Examples:

- DC01
- FS01

Keeping servers separate from workstations allows different security and management policies to be applied.

---

# Security Groups

Security groups were created to simplify permission management.

| Group | Purpose |
|--------|---------|
| HR | Access to HR resources |
| Finance | Access to Finance resources |
| IT | Access to IT resources |
| Sales | Access to Sales resources |
| Management | Access to Management resources |

Rather than assigning permissions directly to individual users, permissions are assigned to groups following Microsoft's recommended best practices.

---

# User Accounts

User accounts were created for employees within their respective departmental Organizational Units.

Each user:

- Has a unique username
- Belongs to a departmental security group
- Authenticates using Active Directory
- Receives Group Policy settings automatically
- Accesses departmental shared folders based on group membership

---

# Computer Accounts

Each workstation was joined to the domain.

Successfully joined computers include:

- PC01
- PC02
- PC03

Server computer accounts include:

- DC01
- FS01

Computer objects are stored within the appropriate Organizational Units for easier administration.

---

# Domain Join Process

Each Windows client was joined to the **kabtech.local** domain using the following process:

1. Configure the client to use the Domain Controller as its DNS server.
2. Verify connectivity to the Domain Controller.
3. Join the computer to the domain.
4. Restart the computer.
5. Sign in using a domain account.
6. Move the computer account into the appropriate Organizational Unit.

Once joined, clients began receiving Group Policy settings and domain authentication services.

---

# Authentication Process

When a user signs in:

1. The workstation contacts the Domain Controller.
2. DNS resolves the Domain Controller's hostname.
3. Active Directory validates the user's credentials.
4. Group memberships are evaluated.
5. Group Policy Objects are applied.
6. Network drives and permissions are assigned.

This centralized authentication process eliminates the need for separate local user accounts on each workstation.

---

# Benefits of the OU Design

The Organizational Unit structure provides several administrative advantages:

- Simplified user management
- Department-specific Group Policies
- Easier troubleshooting
- Improved scalability
- Logical separation of users and computers
- Easier delegation of administrative tasks

---

# Active Directory Administration Tools

The following tools were used during deployment and administration.

| Tool | Purpose |
|------|---------|
| Active Directory Users and Computers | Manage users, groups, computers, and OUs |
| Active Directory Administrative Center | Modern AD management interface |
| Group Policy Management | Configure and deploy Group Policies |
| Server Manager | Install and manage AD DS |

---

# Active Directory Validation

The following tasks were successfully completed:

- Installed Active Directory Domain Services.
- Promoted DC01 to a Domain Controller.
- Created the **kabtech.local** domain.
- Created Organizational Units.
- Created departmental security groups.
- Added users to their respective groups.
- Joined Windows clients to the domain.
- Verified successful domain authentication.
- Managed users and computers through Active Directory Users and Computers.

---

# Summary

Active Directory provides the foundation for centralized management within the Windows Server 2022 Enterprise IT Lab. By organizing users, computers, and security groups into a structured hierarchy, the environment supports efficient administration, secure authentication, scalable growth, and consistent policy enforcement across the enterprise.
