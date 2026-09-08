Phishing Analysis

Phishing is the number one attack vector. 90 percent of breaches start with a phishing email. SOC analysts must analyze these emails to prevent credential theft.

How to Analyze an Email Header

When you receive a suspicious email, look at the full header. In Gmail, click Show Original.
Check the From field. Compare it to the Reply-To field. If they do not match, the email is spoofed.
Check the Received field to see which country the email originated from.

Safe Tools for Analyzing Suspicious Links

VirusTotal (virustotal.com): Copy and paste a suspicious URL into this tool. It scans the link against over 70 security vendors and tells you if it is malicious.

URLScan.io: This tool opens the website in a safe sandbox and takes a screenshot. You can see the site behavior without actually visiting it.

Real-World SOC Scenario

An employee reports an email claiming to be from the CEO asking for bank details.
As a SOC analyst, you extract the domain from the email. You paste it into VirusTotal and discover it is flagged as malicious.
Your action is to block the domain across the entire email gateway and advise the employee to delete the email.
