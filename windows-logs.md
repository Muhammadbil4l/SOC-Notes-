Windows Event Log Analysis for SOC Analysts

The Windows Event Viewer is the primary source of investigation for a SOC analyst. Below are the critical Event IDs you must memorize.

Accessing Logs:
Open Run (Windows + R) and type "eventvwr.msc" to open Event Viewer.
Navigate to Windows Logs > Security for authentication logs.

Critical Event IDs to Memorize:

Event ID 4624: Successful Logon
Meaning: A user successfully logged into the system.
SOC Significance: Monitor for logins occurring outside of normal business hours (e.g., 2 AM). Check the Logon Type:
Type 2: Interactive (user physically at the keyboard).
Type 3: Network (accessing shared folders).
Type 10: Remote Interactive (RDP).

Event ID 4625: Failed Logon
Meaning: A user failed to log in.
SOC Significance: A sudden burst of 50+ failed logins in 5 minutes indicates a Brute Force attack. If this is followed immediately by a 4624 (success) from the same source IP, the attacker has successfully broken in.

Event ID 4720: User Account Created
Meaning: A new local user account was created.
SOC Significance: Attackers often create hidden accounts (ending with a dollar sign, e.g., "hacker$") to maintain persistence. Immediately verify with HR if a new account appears.

Event ID 4732: User Added to Privileged Group
Meaning: A user was added to a security-enabled local group (like Administrators).
SOC Significance: An attacker will escalate their privileges. If a standard user is suddenly added to the Administrators group, treat it as a compromise.

Event ID 4768: Kerberos TGT Requested
Meaning: Authentication request for a domain user.
SOC Significance: Attackers use tools like Mimikatz for Kerberos attacks. Unusual TGT requests from non-domain devices are suspicious.

What to Look For as a SOC Analyst:
1. Time Stamps: Is this login occurring at 3 AM?
2. Source IP: Is the login coming from an external country where we have no office?
3. User Account: Does this account actually belong to an employee who works this shift?

Basic Investigation Flow:
If you see a high number of 4625 failures from IP 45.x.x.x, block that IP on the firewall immediately.
If you see a 4624 success from an external IP after many failures, force a password reset for that user immediately.
