# Phase 10: Domain-Joined Windows Client Deployment


## Objective

The objective of this phase was to deploy a Windows 11 Enterprise workstation and integrate it into the existing Active Directory environment.

This simulates how organizations connect employee devices to a centralized domain for authentication, management, and security enforcement.


## Client Workstation Configuration

A new virtual machine was created using VMware Workstation to represent an employee endpoint.

### CLIENT01

Operating System:
- Windows 11 Enterprise Evaluation

Network:
- VMware Host-only Network (VMnet2)

IP Address:
- 192.168.10.20

DNS Server:
- 192.168.10.10 (Domain Controller)


## Domain Join Process

The workstation was joined to the existing Active Directory domain:

Domain:

igor.local


After successful authentication with the domain administrator account, CLIENT01 became a managed endpoint inside the corporate environment.


## Active Directory Integration

After joining the domain, the workstation automatically appeared inside Active Directory Users and Computers.

The computer object was moved from the default Computers container into the dedicated Workstations Organizational Unit.

Structure:

igor.local

├── Workstations
│   └── CLIENT01


## What I Learned

### Domain Authentication

I learned how enterprise environments use Active Directory to centralize authentication instead of managing accounts locally on every machine.

Users can authenticate from different devices using their domain credentials.


### DNS and Active Directory Relationship

One of the most important concepts learned in this phase was the dependency between Active Directory and DNS.

The client workstation needed to use the Domain Controller as its DNS server in order to locate domain services and successfully join the domain.


### Endpoint Management

This phase introduced how organizations manage employee devices through centralized infrastructure.

A domain-joined workstation allows administrators to later apply:

- Group Policy settings
- Security configurations
- User restrictions
- Endpoint monitoring


## Deployment Evidence

### Domain-Joined Windows Client

The screenshot below demonstrates that CLIENT01 successfully joined the corp.local domain.

!(windows-joined-domain.png)


### Computer Object in Active Directory

The screenshot below shows CLIENT01 registered inside the Workstations Organizational Unit.

!(active-directory.png)


### Domain User Authentication

The screenshot below demonstrates successful login using a domain user account.

!(login-to-domain.png)


## Next Steps

The next phase will focus on improving the security of the environment by implementing:

- Group Policy security settings
- Password policies
- Account lockout policies
- Auditing and monitoring
