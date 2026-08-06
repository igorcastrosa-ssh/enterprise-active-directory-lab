# Lessons Learned

## Overview

Throughout the development of this Active Directory and SOC monitoring lab, several technical challenges were encountered during deployment, configuration, and security testing.

Resolving these issues improved my understanding of enterprise infrastructure, Windows administration, networking, and security monitoring.

---

# VMware Networking Troubleshooting

## Problem

Initial communication issues occurred between virtual machines due to network configuration and adapter settings.

## Resolution

Troubleshooting included:

* Reviewing VMware virtual network configuration
* Verifying VMnet settings
* Checking IP addressing
* Testing connectivity between systems
* Validating DNS resolution

## Key Takeaway

Proper network planning is critical before deploying enterprise services. Small configuration errors can prevent communication between systems and affect services such as Active Directory.

---

# Active Directory and DNS Troubleshooting

## Problem

Domain communication issues occurred when configuring clients and joining systems to the domain.

## Resolution

Verified:

* Domain Controller availability
* DNS configuration
* Client DNS settings
* Network connectivity

## Key Takeaway

Active Directory depends heavily on DNS. Correct DNS configuration is required for domain discovery, authentication, and communication with Domain Controllers.

---

# Wazuh Agent Troubleshooting

## Problem

Windows endpoints were successfully installed with Wazuh agents but initially did not appear in the Wazuh dashboard.

## Resolution

Troubleshooting steps included:

* Verifying agent registration
* Checking manager connectivity
* Restarting Wazuh services
* Reviewing agent logs

## Key Takeaway

SIEM deployments require proper communication between endpoints and the monitoring server. Agent connectivity should always be validated before investigating missing alerts.

---

# Missing Security Events

## Problem

Some expected Windows security events were not appearing during testing.

## Resolution

Reviewed:

* Group Policy auditing settings
* Advanced Audit Policy Configuration
* Windows Event Viewer logs
* Event generation procedures

## Key Takeaway

Security monitoring depends on properly configured logging. Before creating detections, ensure the required telemetry is being generated and collected.

---

# Detection Testing Improvements

## Problem

Initial testing required adjustments to ensure security events generated meaningful alerts.

## Resolution

Created controlled tests for:

* Failed authentication attempts
* User creation
* Privileged group changes
* File modifications
* Suspicious PowerShell activity

## Key Takeaway

Detection engineering requires both technical configuration and validation. A security control is only effective when it can reliably identify the activity it was designed to detect.

---

# Overall Skills Developed

This project strengthened my experience with:

* Active Directory administration
* Windows security configuration
* Group Policy management
* DNS troubleshooting
* SIEM deployment
* Security event analysis
* Detection validation
* Troubleshooting enterprise environments
