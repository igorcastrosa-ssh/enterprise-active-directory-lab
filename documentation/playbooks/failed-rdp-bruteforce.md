Detecting Failed RDP Brute Force Attempts

Objective: Detect repeated failed authentication attempts over Remote Desktop.

Relevant Events: 4625

MITRE ATT&CK: T1110 – Brute Force

Investigation Steps
1. Identify username.
2. Identify source IP.
3. Count failed attempts.
4. Determine whether the account later logged in successfully.
5. Check for PowerShell execution.
6. Check for persistence creation.
7. Escalate if suspicious.

Response
Lock account if necessary.
Reset password.
Block offending IP.
Review lateral movement.
