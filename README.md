# It-Solera-Internship-task-1
Deployed Wazuh SIEM in a virtual lab using Ubuntu Server as Manager and Kali Linux as Agent. Configured File Integrity Monitoring (FIM) to track critical directories in real-time and detect file creation, modification, and deletion events. Verified alerts through the Wazuh Dashboard and resolved configuration and synchronization issues.

Wazuh Installation & File Integrity Monitoring (FIM)

## 📌 Project Overview
This project demonstrates the installation and configuration of Wazuh SIEM in a virtual lab environment and the implementation of File Integrity Monitoring (FIM).

The objective was to connect a Kali Linux agent with a Wazuh Manager (Ubuntu Server) and monitor critical directories for unauthorized file changes such as creation, modification, and deletion.

---

## 🎯 Objectives
- Deploy Wazuh Manager on Ubuntu Server
- Deploy and connect Wazuh Agent (Kali Linux)
- Configure File Integrity Monitoring (FIM)
- Monitor critical directories in real-time
- Generate and validate alerts in Wazuh Dashboard
- Troubleshoot configuration and synchronization issues

---

## 🖥️ Lab Environment

### Virtual Machine 1 – Wazuh Manager
- OS: Ubuntu Server 22.04 LTS
- RAM: 4 GB
- CPU: 2 vCPUs
- Network: NAT

### Virtual Machine 2 – Wazuh Agent
- OS: Kali Linux
- RAM: 2 GB
- CPU: 2 vCPUs
- Network: NAT

### Tools Used
- VMware Workstation
- Ubuntu Server ISO
- Kali Linux ISO
- Wazuh 4.x

---

## ⚙️ Wazuh Manager Installation

The official Wazuh installation script was used:

```bash
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh && sudo bash ./wazuh-install.sh -a

This installed:

Wazuh Manager

Wazuh Indexer

Wazuh Dashboard

🔗 Wazuh Agent Deployment

The agent was installed on Kali Linux and connected to the Wazuh Manager.

After installation:

sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent

Agent connectivity was verified via the Wazuh Dashboard.

🔐 File Integrity Monitoring (FIM) Configuration

The ossec.conf file was modified to monitor a specific directory:

sudo nano /var/ossec/etc/ossec.conf

Added inside <syscheck>:

<directories check_all="yes" realtime="yes">
/home/shadow-null/Desktop/r
</directories>

Services were restarted:

sudo service wazuh-agent restart
sudo service wazuh-manager restart
🧪 Testing & Validation

The following actions were performed:

Created a test file

Modified the file content

Deleted the file

All actions generated alerts in the Wazuh Dashboard under the File Integrity Monitoring module.

⚠️ Challenges & Solutions
1. XML Configuration Error

Issue: Wazuh Manager failed to restart due to incorrect XML syntax.
Solution: Reviewed ossec.log and corrected the configuration file.

2. Time Synchronization Issue

Issue: Alerts were not visible immediately.
Solution: Adjusted dashboard time filter to view all alerts.

3. Permission Denied Errors

Issue: Some commands failed due to insufficient privileges.
Solution: Used sudo for administrative access.

📊 Key Learning Outcomes

Practical understanding of Wazuh architecture

Hands-on experience with FIM configuration

Real-time security monitoring

Log analysis and troubleshooting

Linux system administration skills

✅ Conclusion

The lab successfully demonstrated real-time File Integrity Monitoring using Wazuh. The system accurately detected file additions, modifications, and deletions, helping strengthen practical SOC monitoring skills.
