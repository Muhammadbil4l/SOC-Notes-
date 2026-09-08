Nmap Cheatsheet for Network Reconnaissance

Nmap is the industry standard for network discovery. SOC analysts use it to audit their own network (find open ports) just as much as attackers use it for reconnaissance.

Scan Types and Commands:

Ping Sweep (Host Discovery):
nmap -sn 192.168.1.0/24
Purpose: Find all active hosts (devices) on the network.
SOC Use: Identify unauthorized machines connected to the network. If a new MAC address appears, investigate.

Version Detection:
nmap -sV 192.168.1.10
Purpose: Identify the service and version running on open ports.
SOC Use: Check if a service is outdated (e.g., Apache 2.2, which has known vulnerabilities).

Aggressive OS Detection:
nmap -A 192.168.1.10
Purpose: Combines OS detection, version detection, and traceroute.
SOC Use: Confirm the operating system of a suspect host (e.g., is it really Windows 10 or just a VM impersonating it?).

Port Scanning:
nmap -p 1-1000 192.168.1.10
Purpose: Scan only the top 1000 most common ports for speed.
SOC Use: Quickly check if critical ports (like 445 SMB or 3389 RDP) are exposed.

Script Scanning:
nmap --script smb-vuln-ms17-010 192.168.1.10
Purpose: Run specific scripts to check for known vulnerabilities.
SOC Use: Check if a Windows machine is vulnerable to EternalBlue (WannaCry).

Important Rule for SOC Analysts:
Never run Nmap against an organization's network without written authorization. In a SOC environment, scanning is usually automated but strictly controlled. Always verify the scope before scanning.
