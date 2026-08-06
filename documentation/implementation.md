# Active Directory Environment Implementation

## Objective

The objective of this phase was to build the foundation of an enterprise-style Active Directory environment by deploying a Windows Server Domain Controller and integrating a managed Windows workstation.

The environment simulates a small corporate network where centralized authentication, endpoint management, and security policies can be applied.

---

# Infrastructure Setup

The lab was created using VMware Workstation Pro using an isolated host-only network.

## Virtual Environment

| System | Role | Operating System |
|---|---|---|
| DC01 | Domain Controller | Windows Server 2022 Evaluation |
| CLIENT01 | Domain-Joined Workstation | Windows 11 Enterprise Evaluation |

## Network Configuration

The environment was configured with static IP addressing to ensure reliable communication between systems.

Configuration:

- DC01 configured with a static IP address
- CLIENT01 configured with a static IP address
- Both systems configured to use the Domain Controller as the DNS server

Active Directory relies heavily on DNS for authentication, domain discovery, and locating network resources.

---

# Domain Controller Deployment

## Installed Roles

The following Windows Server roles were installed:

- Active Directory Domain Services (AD DS)
- DNS Server

After installation, DC01 was promoted to a Domain Controller and a new Active Directory forest was created.

Domain: igor.local


The Domain Controller became responsible for:

- User authentication
- Active Directory directory services
- Domain security policies
- DNS services

---

# Active Directory Structure

After deploying Active Directory, organizational units, users, and security groups were created to simulate an enterprise environment.

Example structure:
igor.local

├── Domain Controllers
│
├── Workstations
│ └── CLIENT01
│
├── Users
│
└── Security Groups


---

# Domain-Joined Workstation Deployment

A Windows 11 workstation was deployed to represent an employee endpoint inside the organization.

CLIENT01 was configured to communicate with the Domain Controller and successfully joined the Active Directory domain.

After joining the domain:

- CLIENT01 appeared inside Active Directory Users and Computers
- The computer object was moved into the Workstations Organizational Unit
- Domain authentication was validated using a domain user account

This simulated how organizations connect and manage employee devices through centralized identity infrastructure.

---

# Implementation Evidence

## Domain Controller Deployment

<img width="1004" height="477" alt="Screenshot 2026-08-05 231853" src="https://github.com/user-attachments/assets/ec1008ce-6e93-49be-be7a-7b68a459fe88" />


## Active Directory Structure

<img width="1020" height="740" alt="ad-showing-ou" src="https://github.com/user-attachments/assets/94e58fae-0546-4608-80f0-ef4c063fd180" />


## Domain-Joined Workstation

<img width="1021" height="762" alt="active-directory" src="https://github.com/user-attachments/assets/9df38a35-8aac-4c1d-824e-f0a2578514a9" />


## Domain User Authentication

<img width="991" height="607" alt="domain login page" src="https://github.com/user-attachments/assets/c9694cec-ec3f-47b8-88df-02bd74ce83c2" />


---

# Key Concepts Learned

## Centralized Identity Management

Active Directory provides centralized management of:

- Users
- Computers
- Authentication
- Permissions
- Security policies

This allows administrators to manage enterprise environments without configuring every machine individually.

---

## DNS and Active Directory Relationship

A major concept learned during deployment was the dependency between Active Directory and DNS.

Domain-joined systems rely on DNS to locate:

- Domain Controllers
- Authentication services
- Internal resources

Incorrect DNS configuration can prevent devices from joining or communicating with the domain.

---

## Enterprise Endpoint Management

Joining CLIENT01 to the domain demonstrated how organizations manage employee workstations through centralized infrastructure.

This foundation enables:

- Group Policy deployment
- Security hardening
- Endpoint monitoring
- Centralized configuration management
