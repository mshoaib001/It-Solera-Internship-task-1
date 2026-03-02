# It-Solera-Internship-task-1
Deployed Wazuh SIEM in a virtual lab using Ubuntu Server as Manager and Kali Linux as Agent. Configured File Integrity Monitoring (FIM) to track critical directories in real-time and detect file creation, modification, and deletion events. Verified alerts through the Wazuh Dashboard and resolved configuration and synchronization issues.

# Wazuh Installation & File Integrity Monitoring (FIM)

## 📌 Project Overview
This project demonstrates the deployment of Wazuh SIEM in a virtual lab environment and the implementation of File Integrity Monitoring (FIM).  
An Ubuntu Server was configured as the Wazuh Manager, and a Kali Linux machine was deployed as the Wazuh Agent. Critical directories were monitored in real-time to detect unauthorized file changes.

---

## 🎯 Objectives
- Deploy Wazuh Manager on Ubuntu Server  
- Connect Kali Linux as Wazuh Agent  
- Configure File Integrity Monitoring (FIM)  
- Monitor critical directories in real-time  
- Generate and validate security alerts  

---

## 🖥️ Lab Environment

### Wazuh Manager (Server)
- **OS:** Ubuntu Server 22.04 LTS  
- **RAM:** 4 GB  
- **CPU:** 2 vCPUs  
- **Network:** NAT  

### Wazuh Agent
- **OS:** Kali Linux  
- **RAM:** 2 GB  
- **CPU:** 2 vCPUs  
- **Network:** NAT  

### Tools Used
- VMware Workstation  
- Wazuh 4.x  
- Ubuntu Server ISO  
- Kali Linux ISO  

---

## ⚙️ Wazuh Manager Installation

```bash
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
```

This command installs:
- Wazuh Manager  
- Wazuh Indexer  
- Wazuh Dashboard  

---

## 🔗 Wazuh Agent Deployment

After downloading the agent package, the following commands were executed:

```bash
sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```

Agent connectivity was verified through the Wazuh Dashboard.

---

## 🔐 File Integrity Monitoring (FIM) Configuration

### Edit Configuration File

```bash
sudo nano /var/ossec/etc/ossec.conf
```

### Add the Following Inside `<syscheck>` Section

```xml
<directories check_all="yes" realtime="yes">
/home/shadow-null/Desktop/r
</directories>
```

### Restart Services

```bash
sudo service wazuh-agent restart
sudo service wazuh-manager restart
```

---

## 🧪 Testing & Validation

The following actions were performed inside the monitored directory:

- Created a test file  
- Modified the file content  
- Deleted the file  

All actions successfully generated alerts in the **Wazuh Dashboard → File Integrity Monitoring (FIM)** module.

---

## ⚠️ Challenges & Solutions

### 1️⃣ XML Configuration Error
- **Issue:** Wazuh Manager failed to restart due to incorrect XML syntax.  
- **Solution:** Reviewed `ossec.log`, corrected syntax error, and restarted the service.

### 2️⃣ Time Synchronization Issue
- **Issue:** Alerts were not visible immediately.  
- **Solution:** Adjusted dashboard time filter to "Last 24 Hours".

### 3️⃣ Permission Denied Errors
- **Issue:** Some commands failed due to insufficient privileges.  
- **Solution:** Used `sudo` to execute administrative commands.

---

## 📊 Key Learning Outcomes
- Understanding of Wazuh architecture  
- Hands-on experience with FIM configuration  
- Real-time security monitoring  
- Log analysis and troubleshooting  
- Linux system administration skills  

---

## ✅ Conclusion
This lab successfully demonstrated real-time File Integrity Monitoring using Wazuh.  
The system accurately detected file creation, modification, and deletion events, strengthening practical SOC monitoring and incident response skills.
