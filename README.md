# Enterprise Active Directory Security Lab with Wazuh Monitoring

## Overview

This project documents the design, deployment, hardening, and monitoring of an enterprise-style Active Directory environment.

The goal of this lab was to simulate a small corporate Windows environment while implementing security controls, centralized identity management, security auditing, and SIEM monitoring.

The environment evolved from a traditional Active Directory infrastructure project into a Security Operations Center (SOC) monitoring lab by integrating Wazuh for detection and analysis of security events.

---

# Project Objectives

- Deploy an enterprise-style Active Directory environment
- Configure centralized authentication and authorization
- Implement security hardening through Group Policy
- Enable Windows security auditing
- Deploy SIEM monitoring using Wazuh
- Generate and investigate security events
- Simulate attacks and validate detections

---

# Lab Architecture

## Environment Overview

The lab consists of multiple virtual machines connected through an isolated VMware network.

| System | Role |
|---|---|
| DC01 | Windows Server Domain Controller |
| CLIENT01 | Windows Client Machine |
| Ubuntu Server | Wazuh Manager / SIEM |

<img width="1264" height="843" alt="Gemini_Generated_Image_gmh1y0gmh1y0gmh1" src="https://github.com/user-attachments/assets/2a2ed443-67a3-4309-bc6d-cfcff3feb67c" />

---

# Technologies Used

## Infrastructure

- VMware Workstation Pro
- Windows Server
- Windows 10/11 Client
- Ubuntu Server

## Identity & Security

- Active Directory Domain Services
- DNS
- Group Policy
- Windows Event Logging
- Security Auditing

## Monitoring

- Wazuh SIEM/XDR
- Wazuh Agents
- File Integrity Monitoring
- Security Alert Analysis

## Scripting

- PowerShell
- Python

---

# Implementation Phases

# Phase 1 - Virtual Infrastructure Setup

## Completed Tasks

- Created isolated VMware network environment
- Installed required operating systems
- Configured static IP addressing
- Established communication between virtual machines

## Skills Demonstrated

- Virtual networking
- Operating system deployment
- Network troubleshooting

<img width="164" height="114" alt="image" src="https://github.com/user-attachments/assets/1d123ba8-06eb-48ae-b32e-fc7b1eebb5d2" />


---

# Phase 2 - Active Directory Deployment

## Completed Tasks

- Installed Windows Server Domain Services
- Promoted server to Domain Controller
- Created Active Directory domain
- Configured DNS services

## Skills Demonstrated

- Active Directory administration
- Domain controller management
- DNS configuration

<img width="1004" height="477" alt="image" src="https://github.com/user-attachments/assets/79e350a7-b25d-42b3-bc75-7ba51d9c7f2e" />


<img width="754" height="526" alt="image" src="https://github.com/user-attachments/assets/089ec6a6-f4f8-4696-8bad-3bddcd99b47e" />


---

# Phase 3 - Identity Management

## Completed Tasks

Created and organized:

- Domain users
- Security groups
- Administrative accounts
- User permissions

Implemented basic enterprise identity structure to simulate organizational access management.

## Skills Demonstrated

- User provisioning
- Group management
- Access control concepts

<img width="750" height="529" alt="image" src="https://github.com/user-attachments/assets/3fd3f2cc-a358-47c2-89a0-1637577fdf5a" />


---

# Phase 4 - Active Directory Hardening

## Completed Tasks

Implemented security improvements using Group Policy:

- Password complexity requirements
- Account lockout policies
- Security baseline configurations
- Administrative restrictions
- Improved endpoint security settings

## Skills Demonstrated

- Windows hardening
- Group Policy management
- Enterprise security configuration

<img width="790" height="581" alt="Screenshot 2026-08-04 220101" src="https://github.com/user-attachments/assets/1241d06a-9c50-4052-a736-c96bb6ecc1e5" />

(Password policies used as example)
---

# Phase 5 - Windows Security Auditing

## Completed Tasks

Configured Windows auditing to collect security-related events.

Monitored important Windows Event IDs:

| Event ID | Description |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon attempt |
| 4720 | User account created |
| 4728 | User added to security-enabled global group |

## Skills Demonstrated

- Windows event analysis
- Security monitoring fundamentals
- Detection engineering concepts

<img width="617" height="429" alt="failed-login-log" src="https://github.com/user-attachments/assets/e663d5ba-4b76-47ef-acd8-18746109147c" />


---

# Phase 6 - Wazuh SIEM Deployment

## Completed Tasks

Deployed Wazuh monitoring infrastructure:

- Installed Wazuh Manager on Ubuntu Server
- Connected Windows endpoints using Wazuh agents
- Verified agent communication
- Configured monitoring capabilities

Monitored:

- Authentication events
- User creation events
- Privilege changes
- File integrity changes
- Suspicious activity

<img width="1451" height="678" alt="wazuh-dashboard-with-active-machiens" src="https://github.com/user-attachments/assets/4db4ef2b-4e56-46f0-9be6-55a083d09613" />


<img width="1451" height="761" alt="wazuh-collecting-account-changes-logs" src="https://github.com/user-attachments/assets/04e6f14e-53f0-49ab-91b6-f082aa96982f" />

---

# Phase 7 - Detection Testing and Attack Simulation

To validate monitoring capabilities, security events were intentionally generated and investigated.

---

## Brute Force Simulation

### Activity

Multiple failed authentication attempts were generated against a Windows account.

### Detection

Detected through:

```
Event ID 4625
```

### Result

Wazuh successfully generated alerts for failed authentication activity.

<img width="1465" height="772" alt="simulated-failed-login-attempt-dashboard-wazuh" src="https://github.com/user-attachments/assets/608ff05c-9cc9-4dc0-ad5b-3012bc921a4d" />


---

## Privilege Change Detection

### Activity

A user was added to a privileged security group.

### Detection

Detected through:

```
Event ID 4728
```

### Result

Wazuh identified changes to privileged group membership.

<img width="1451" height="761" alt="wazuh-collecting-account-changes-logs" src="https://github.com/user-attachments/assets/ba0210fa-c442-49ac-ba8a-3db819f4652f" />


---

## User Creation Detection

### Activity

A new domain user account was created.

### Detection

Detected through:

```
Event ID 4720
```

### Result

Account creation activity was logged and analyzed.

<img width="1029" height="26" alt="image" src="https://github.com/user-attachments/assets/17a8a82a-e1fb-4c6f-97e6-0fd67a2fa35b" />


---

# File Integrity Monitoring

## Completed Tasks

Configured Wazuh File Integrity Monitoring (FIM) to detect changes to monitored directories.

Testing included:

- Creating files
- Modifying files
- Removing files

## Result

Wazuh successfully detected file modifications and generated security events.

<img width="673" height="630" alt="file-change-detected pt2" src="https://github.com/user-attachments/assets/a0557525-cc84-4f69-9088-96bea8eb91de" />

---

# Troubleshooting and Lessons Learned

## Wazuh Agent Connection Issues

### Problem

Windows agents were installed but initially did not appear in the Wazuh dashboard.

### Resolution

- Verified manager IP configuration
- Checked agent registration
- Restarted services
- Validated network communication

---

## Missing Windows Security Events

### Problem

Certain security events were not appearing.

### Resolution

- Reviewed audit policies
- Updated Group Policy settings
- Generated test activity
- Verified logs through Event Viewer and Wazuh

---

## VMware Networking Issues

### Problem

Virtual machines experienced communication issues.

### Resolution

- Reviewed VMware network adapters
- Verified static addressing
- Tested DNS resolution
- Confirmed connectivity between systems

---

# Skills Demonstrated

Through this project I practiced:

## Active Directory

- Domain deployment
- User/group management
- DNS administration
- Group Policy configuration

## Security Operations

- SIEM deployment
- Log analysis
- Detection validation
- Security event investigation

## Windows Security

- Audit policy configuration
- Event ID analysis
- Hardening techniques

## Troubleshooting

- Network debugging
- Service troubleshooting
- Configuration analysis

---

# Future Improvements

Planned improvements:

- Add additional Windows endpoints
- Create custom Wazuh detection rules
- Integrate MITRE ATT&CK mappings
- Automate attack simulations
- Expand SOC monitoring capabilities

---

# Final Project Summary

This project demonstrates the process of building, securing, and monitoring an enterprise-style Windows environment.

Starting as an Active Directory administration lab, it evolved into a SOC-focused security monitoring environment by integrating Wazuh, implementing security controls, and validating detections through controlled attack simulations.
