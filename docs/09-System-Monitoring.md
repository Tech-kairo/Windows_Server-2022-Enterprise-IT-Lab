docs/09-System-Monitoring.md


# System Monitoring

## Overview

System monitoring is an essential responsibility of an IT administrator. It helps ensure that servers and workstations remain healthy, reliable, and available. During this lab, several built-in Windows monitoring tools were used to monitor performance, review system health, troubleshoot issues, and manage services.

---

# Environment

| Setting | Value |
|---------|-------|
| Domain | kabtech.local |
| Domain Controller | DC01 |
| File Server | FS01 |
| Client Computers | PC01, PC02 |
| Operating System | Windows Server 2022 / Windows 11 |

---

# Monitoring Tools Used

The following Windows administration tools were used throughout the lab.

| Tool | Purpose |
|------|---------|
| Task Manager | Monitor running processes and system performance |
| Resource Monitor | Analyse CPU, memory, disk and network usage |
| Performance Monitor | Monitor performance counters |
| Reliability Monitor | Review system stability and failures |
| Event Viewer | Investigate Windows events and errors |
| Windows Admin Center | Remote monitoring and management |
| Services Console | Manage Windows services |

---

# Task Manager

Task Manager was used to monitor:

- CPU usage
- Memory utilisation
- Disk activity
- Network utilisation
- Running applications
- Background processes

Task Manager provides a quick overview of system resource consumption.

---

# Resource Monitor

Resource Monitor provides detailed information about system resource usage.

The following resources were monitored:

- CPU
- Memory
- Disk
- Network

This tool helps identify applications consuming excessive resources.

---

# Performance Monitor

Performance Monitor was used to observe system performance over time.

Common counters include:

- Processor Time
- Available Memory
- Disk Queue Length
- Network Interface Throughput

Performance Monitor is useful for identifying trends and diagnosing performance issues.

---

# Reliability Monitor

Reliability Monitor provides a timeline of system stability.

It records:

- Application crashes
- Windows failures
- Hardware failures
- Windows Updates
- Software installations

This tool helps identify when problems first occurred.

---

# Event Viewer

Event Viewer was used to investigate Windows logs.

The following log categories were reviewed:

- Application
- Security
- System
- Windows Logs

Event Viewer is a critical troubleshooting tool for identifying errors and warnings.

---

# Windows Services

The Services console was used to review and manage Windows services.

Examples include:

- DHCP Server
- DNS Server
- Windows Update
- Print Spooler
- Windows Time
- Server Service

Administrators can start, stop, restart and configure services as needed.

---

# Windows Admin Center Monitoring

Windows Admin Center provided centralised monitoring of managed devices.

Features used included:

- Performance monitoring
- Event logs
- Remote PowerShell
- Service management
- Hardware information
- Storage monitoring

---

# Health Checks

The following health checks were completed during the project.

## Network Connectivity

Verified communication between:

- DC01
- FS01
- PC01
- PC02

using:

```powershell
ping
```

---

## DNS

Verified name resolution using:

```powershell
nslookup
```

---

## DHCP

Confirmed clients received addresses automatically using:

```powershell
ipconfig /all
```

---

## Group Policy

Verified successful Group Policy application using:

```powershell
gpresult /r
```

---

## Active Directory

Confirmed users, computers and security groups were functioning correctly.

---

# Routine Maintenance

Regular maintenance tasks performed during the lab included:

- Reviewing Event Viewer logs
- Monitoring system performance
- Checking Windows services
- Installing Windows updates
- Verifying Group Policy
- Testing network connectivity
- Confirming DNS functionality

---

# Benefits

Effective monitoring provides:

- Early detection of issues
- Faster troubleshooting
- Improved system reliability
- Better resource management
- Reduced downtime
- Improved security
- Better user experience

---

# Summary

System monitoring plays a vital role in maintaining a healthy Windows Server environment. Throughout this lab, built-in Windows administration tools were used to monitor performance, troubleshoot issues, verify system health, and maintain reliable operation of servers and client computers.
