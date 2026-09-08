MITRE ATT&CK Framework

MITRE ATT&CK is a globally recognized knowledge base of adversary tactics and techniques. It provides a common language for SOC teams to describe what an attacker is doing.

Structure of the Framework

Tactics: The attackers goal (the why). For example, Initial Access, Execution, or Exfiltration.
Techniques: The specific method used to achieve the goal (the how). For example, Phishing is a technique under Initial Access.

The 6 Key Tactics You Must Memorize

1. Initial Access: How the attacker gets in (Phishing, Exploiting vulnerabilities).
2. Execution: How they run their malicious code (PowerShell, command line).
3. Persistence: How they stay in the system after a reboot (Registry Run keys, scheduled tasks).
4. Privilege Escalation: How they gain administrator rights.
5. Lateral Movement: How they move from one computer to another inside the network.
6. Exfiltration: How they steal the data out of the network.

How to Use MITRE in an Interview

If you see a suspicious PowerShell command executing from a temporary folder, you can say: This maps to the Execution tactic. I would check MITRE for technique T1059.001 (Command and Scripting Interpreter). This helps the team understand the attack pattern faster.
