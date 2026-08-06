# Architecture

## Overview

The Enterprise Active Directory Security & Monitoring Lab was designed to simulate a small enterprise Windows environment focused on identity management, endpoint security, centralized monitoring, and attack detection.

The environment consists of three virtual machines connected through an isolated internal network:

* **DC01** – Windows Server Domain Controller
* **CLIENT01** – Windows 11 Enterprise Workstation
* **Ubuntu Server** – Wazuh SIEM Platform

This architecture demonstrates how enterprise Windows environments authenticate users, apply centralized security policies, generate security telemetry, and forward events to a Security Information and Event Management (SIEM) platform for monitoring and investigation.

---

# Lab Architecture

> **Insert the architecture diagram here**

---

# Network Topology

| Machine      | Operating System | IP Address    | Role                              |
| ------------ | ---------------- | ------------- | --------------------------------- |
| DC01         | Windows Server   | 192.168.10.10 | Domain Controller, DNS Server     |
| CLIENT01     | Windows 11       | 192.168.10.20 | Domain-Joined Endpoint            |
| Wazuh Server | Ubuntu Server    | 192.168.10.X  | Wazuh Manager, Indexer, Dashboard |

All systems communicate over an isolated VMware internal network.

---

# Virtual Machine Roles

## DC01 – Domain Controller

DC01 serves as the central identity and management server for the environment.

Responsibilities include:

* Active Directory Domain Services (AD DS)
* Domain Name System (DNS)
* User and Group Management
* Group Policy Management
* Security Policy Enforcement
* Authentication Services

All domain users authenticate through this server.

---

## CLIENT01 – Domain Workstation

CLIENT01 represents a standard enterprise Windows endpoint joined to the Active Directory domain.

Responsibilities include:

* User authentication
* PowerShell execution
* Windows Event generation
* File Integrity Monitoring
* Remote Desktop testing
* SMB access
* Security event generation

The workstation is configured to forward security telemetry to the Wazuh platform.

---

## Ubuntu Server – Wazuh Platform

The Ubuntu server hosts the centralized security monitoring infrastructure.

Components include:

* Wazuh Manager
* Wazuh Dashboard
* Wazuh Indexer

Responsibilities include:

* Receiving events from Windows agents
* File Integrity Monitoring
* Security event correlation
* Alert generation
* Centralized log management
* Security investigations

---

# Event Flow

The following process describes how security events move throughout the environment.

1. Activity occurs on the Windows endpoint or Domain Controller.
2. Windows generates Security, System, or PowerShell events.
3. The Wazuh Agent collects the events locally.
4. Events are securely forwarded to the Wazuh Manager.
5. Wazuh decodes and analyzes the events.
6. Detection rules generate alerts.
7. Alerts become available through the Wazuh Dashboard for investigation.

This workflow mirrors a simplified enterprise Security Operations Center (SOC) monitoring pipeline.

---

# Security Monitoring Architecture

The environment provides centralized visibility into:

* Authentication events
* Account management
* Group membership changes
* PowerShell execution
* Process creation
* Scheduled task creation
* Service installation
* SMB share access
* File Integrity Monitoring (FIM)

Each event is normalized by Wazuh and correlated into searchable alerts.

---

# Security Controls

The lab implements multiple layers of security based on a defense-in-depth approach.

## Identity Security

* Active Directory authentication
* Password policy
* Account lockout policy
* Least privilege administration

## Endpoint Security

* Windows Defender
* Windows Firewall
* Advanced Audit Policies
* PowerShell Script Block Logging
* Process Creation Auditing

## Monitoring

* Wazuh SIEM
* Windows Event Collection
* File Integrity Monitoring
* Authentication Monitoring
* PowerShell Monitoring

---

# Design Decisions

Several architectural decisions were made to better simulate an enterprise environment.

### Dedicated Domain Controller

Separating Active Directory services from client systems reflects common enterprise deployments and centralizes identity management.

### Centralized SIEM

Rather than reviewing Windows Event Viewer locally, all security telemetry is forwarded to Wazuh for centralized analysis and alerting.

### Domain-Joined Workstation

Using a managed endpoint allows Group Policy Objects (GPOs), audit policies, and security configurations to be applied consistently.

### Layered Security

The environment combines preventive controls (Group Policy, Defender, Firewall) with detective controls (Wazuh, audit logging, File Integrity Monitoring) to demonstrate a defense-in-depth strategy.

---

# Conclusion

This architecture provides a practical representation of a small enterprise Windows environment with centralized identity management, security hardening, and security monitoring.

Although simplified for educational purposes, the design follows many of the same principles used in production environments, including centralized authentication, endpoint management, layered security controls, and SIEM-based monitoring.
