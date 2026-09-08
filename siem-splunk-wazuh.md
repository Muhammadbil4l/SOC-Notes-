SIEM Fundamentals for SOC Analysts

SIEM stands for Security Information and Event Management. It is a centralized system that collects logs from firewalls, servers, and endpoints to detect security threats. A SOC analyst spends 90 percent of their time working on the SIEM dashboard.

Splunk Basics

Splunk is a leading SIEM tool. Logs are stored in indexes. You search logs using SPL (Search Processing Language). To find all error logs, you type: index=main error.
To find web server 404 errors, you type: index=main sourcetype=access_combined status=404.
Splunk Free provides 500 MB of data ingestion per day and allows you to upload sample logs for practice.

Wazuh Basics

Wazuh is a free and open-source SIEM. It is perfect for building a home lab.
The installation command on Ubuntu is: curl -sO https://packages.wazuh.com/4.x/wazuh-install.sh && sudo bash wazuh-install.sh -a.
Once installed, you can access the dashboard in your browser at localhost.

SOC Analyst Daily Routine with SIEM

The goal is to create correlation rules. For example, if a single IP fails to login 10 times in 5 minutes, the SIEM triggers an alert. The analyst investigates the alert, verifies if it is a false positive, and if it is real, initiates incident response.
