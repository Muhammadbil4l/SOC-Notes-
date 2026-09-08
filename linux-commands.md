Essential Linux Commands for Log Analysis

As a SOC analyst, you will frequently use Linux systems (like Kali Linux or Wazuh SIEM boxes). Master these commands for daily triage.

Log Analysis Commands:

cat /var/log/auth.log
Purpose: View the authentication logs (login attempts, sudo usage).
SOC Use: Check for "Failed password" entries.

grep "Failed password" /var/log/auth.log
Purpose: Search for all failed login attempts in the authentication log.
SOC Use: Identify brute force attempts. To see the count, use: grep "Failed password" /var/log/auth.log | wc -l

tail -f /var/log/syslog
Purpose: Follow the system log live (streaming).
SOC Use: Monitor real-time alerts or events. Press CTRL + C to exit the streaming.

awk '{print $1}' /var/log/auth.log
Purpose: Print only the first column of a log file (usually the timestamp or IP).
SOC Use: Extract specific fields (like source IPs) from large logs.

Process and System Commands:

ps aux
Purpose: List all running processes.
SOC Use: Identify suspicious processes with high CPU usage or unusual names (e.g., "svchost.exe" on Linux).

netstat -tulpn
Purpose: Display active network ports and connections (-t TCP, -u UDP, -l listening, -p process ID).
SOC Use: Check for any unknown services listening on strange ports (like 1337, 4444).

systemctl status [service_name]
Purpose: Check the status of a specific service.
SOC Use: If a critical service is stopped, investigate the logs.

Find and Search:

find / -name "*.malware" 2>/dev/null
Purpose: Find files with a specific name.
SOC Use: Search for known malware hashes or filenames.

Practical SOC Scenario:
If a user reports a slow PC, an analyst can SSH into the Linux SIEM server and run:
grep "2026-09-08" /var/log/auth.log | grep "Failed password" | wc -l
If the count is high, an attacker is brute-forcing.
Immediate Action: iptables -A INPUT -s [attacker-IP] -j DROP (block the IP).
