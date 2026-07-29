## Objective

Implemented Windows security auditing within the Active Directory environment to improve visibility into user activity, authentication attempts, and security-related changes.

Security logging is an essential component of enterprise environments because it allows administrators and security teams to detect and investigate suspicious activity.


## Audit Policy Configuration

Security auditing was configured through Group Policy using:

- Corporate Security Policy
- Advanced Audit Policy Configuration

Enabled auditing for:

- Logon/Logoff Events
  - Success
  - Failure

- Account Management Events
  - Success
  - Failure

These policies allow monitoring of authentication attempts, user changes, and security group modifications.


## Event Analysis

Security events were generated on CLIENT01 by performing:

- Successful domain authentication
- Failed login attempts

The events were analyzed using:
Event Viewer
------>Windows logs
---------> Security

Important Event IDs identified:

| Event ID | Description |
|----------|-------------|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4720 | User account created |
| 4728 | User added to security group |


## Security Concepts Learned

This phase demonstrated:

- The importance of security logging for threat detection and incident response
- How Group Policy can centrally enforce auditing configurations
- How Windows records authentication activity
- The importance of Role-Based Access Control (RBAC)

During testing, standard users were unable to access security logs, demonstrating how enterprises restrict sensitive security information to authorized administrators.


## Evidence

Screenshots included:

- Security auditing configuration
- Successful authentication event (4624)
- Failed authentication event (4625)


## Next Steps

The next phase will integrate a SIEM platform to collect and analyze Windows security logs, simulating a real Security Operations Center (SOC) monitoring environment.
