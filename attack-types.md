SOC Analyst Attack Reference Guide

This document provides a quick overview of common cyber attacks, their root causes, and the immediate actions a SOC analyst should take.

1. ARP Spoofing (Layer 2)

What it is: The attacker sends fake ARP replies claiming to be the default gateway. All traffic is redirected to the attacker (Man-in-the-Middle).
Root Cause: ARP protocol lacks authentication.
Detection: Duplicate MAC addresses claiming to be the gateway IP.
SOC Action: Isolate the affected victim machine immediately. Enable Dynamic ARP Inspection (DAI) on the network switch.

2. IP Spoofing (Layer 3)

What it is: The attacker manipulates the source IP address in packet headers to hide their identity or impersonate another device.
Root Cause: Routers do not verify the source IP address by default.
Detection: Internal network traffic showing external source IPs.
SOC Action: Implement Ingress and Egress filtering on firewalls to block packets with mismatched source addresses.

3. SYN Flood (Layer 4)

What it is: The attacker sends thousands of SYN requests (TCP handshake initiations) but never completes the ACK. The server's resources are exhausted.
Root Cause: TCP reserves resources for half-open connections.
Detection: High volume of SYN_RECV connections in netstat output.
SOC Action: Enable SYN Cookies on the operating system. Activate rate limiting on the firewall.

4. SQL Injection (Layer 7)

What it is: Malicious SQL code (e.g., ' OR '1'='1) is inserted into application input fields to manipulate the backend database.
Root Cause: Lack of input validation and sanitization by developers.
Detection: WAF logs showing SQL keywords like "union select" or "or 1=1".
SOC Action: Flag the request to the development team. Implement Web Application Firewall (WAF) rules to block suspicious patterns.

5. Phishing (Layer 7)

What it is: A social engineering attack where an attacker sends fraudulent communications (emails/SMS) to trick users into revealing sensitive information.
Root Cause: Human trust and urgency are exploited.
Detection: Reports from users of suspicious emails. Mismatch in "From" and "Reply-To" email headers.
SOC Action: Block the malicious domain/URL. Reset passwords for any users who clicked. Enforce Multi-Factor Authentication (MFA).

6. XSS (Cross-Site Scripting)

What it is: Malicious JavaScript code is injected into a trusted website (e.g., in comment boxes). This script runs in other users' browsers and steals session cookies.
Root Cause: Improper output encoding and input sanitization.
Detection: WAF alerts for HTML script tags (like script, onerror).
SOC Action: Block the suspicious request. Advise the web development team to implement Content Security Policy (CSP).

7. Weak SSL/TLS Exploits

What it is: Servers running outdated protocols like SSL 2.0, SSL 3.0, or TLS 1.0 are vulnerable to downgrade attacks and data decryption.
Root Cause: Poor patching and backward compatibility enabled.
Detection: Vulnerability scanners reporting deprecated TLS versions.
SOC Action: Immediately disable insecure protocols on the server. Enforce TLS 1.2 or 1.3 only.

8. Session Hijacking

What it is: The attacker steals a user's session ID/cookie and impersonates them to gain unauthorized access to an application.
Root Cause: Session IDs transmitted over unencrypted HTTP or stolen via XSS.
Detection: Same session ID being used from two different geographic locations simultaneously.
SOC Action: Immediately invalidate (kill) the active session. Force a password reset for the user.

The Golden Rule
Every major attack exploits a form of trust. ARP trusts MAC addresses, IP trusts source addresses, and SQLi trusts user input. As a SOC analyst, our job is to remove blind trust through strict verification and monitoring.
