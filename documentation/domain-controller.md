#Initial phase 7/21/2026

## Objective

The objective of this phase was to create the foundation of an enterprise Active Directory environment by deploying a Windows Server Domain Controller.


## Environment Setup

The lab was created using VMware Workstation Pro.

Network:

- Network Type: Host-only
- Virtual Network: VMnet2
- Subnet: 192.168.10.0/24

## Virtual Machine Configuration

### DC01

Operating System:
Windows Server 2022 Evaluation

Role:
Domain Controller

Resources:

- 2 CPU cores
- 4GB RAM
- 60GB Storage


## Network Configuration

Static IP configuration:

IP Address:

192.168.10.10

Subnet Mask:

255.255.255.0

DNS:

192.168.10.10

The Domain Controller was configured to use itself as the DNS server because Active Directory relies heavily on DNS for authentication and resource discovery.

## Active Directory Deployment

Installed server roles:

- Active Directory Domain Services
- DNS Server


Created a new forest: igor.local

Domain: IGOR


After installation, the server was promoted to a Domain Controller.


## What I Learned:

### Active Directory

Active Directory is Microsoft's directory service used to manage:

- Users
- Computers
- Authentication
- Permissions
- Policies


### Domain Controllers

A Domain Controller is responsible for:

- Authenticating users
- Storing Active Directory information
- Managing domain security policies


### DNS Importance

I learned that Active Directory depends on DNS.

DNS allows computers inside the domain to locate:

- Domain Controllers
- Authentication services
- Network resources


### Enterprise Networking

I learned how organizations separate internal networks and use centralized identity management instead of managing every computer individually.


## Challenges Encountered

One of the initial challenges was setting up the virtual environment from scratch, as this was my first time independently working with virtualization software and building a Windows Server environment on my own machine.

I had to research VMware networking configurations, virtual machine resource allocation, and Windows Server installation procedures to correctly create an isolated enterprise lab environment.

Although the initial setup required significant troubleshooting and documentation review, the process strengthened my understanding of virtualization concepts, network configuration, and the importance of properly planning infrastructure before deploying enterprise services.

Example:

- Understanding why the Domain Controller needed a static IP
- Configuring VMware networking correctly
- Troubleshooting DNS settings


## Next Steps

The next phase will include:

- Creating Organizational Units
- Adding users and groups
- Joining Windows clients to the domain
- Implementing security policies
