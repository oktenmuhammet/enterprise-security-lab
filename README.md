# Enterprise Security Lab (PCI DSS Oriented)

This project is a self-built enterprise-level cybersecurity lab designed to simulate a real-world PCI DSS environment.

The goal is not only to build systems, but to design, secure, monitor, and detect threats like a real Security Operations Center (SOC).

---

## 🔐 Architecture Overview

The lab is segmented into multiple security zones:

- **Internal Zone** → Active Directory, user machines  
- **DMZ Zone** → Wazuh, Web Server, LDAP, Jump Server, Vault  
- **CDE Zone (Cardholder Data Environment)** → App Server, Database  
- **Attack Zone** → Kali Linux, Metasploitable  
- **Backup Zone** → Backup Server  

All traffic is controlled via **pfSense firewall** with a default deny approach.

---

## 🧰 Technologies Used

- SIEM: Wazuh  
- Firewall: pfSense  
- IDS/IPS: Suricata  
- WAF: ModSecurity (Nginx)  
- Identity: Active Directory, LDAP  
- Secrets Management: HashiCorp Vault  
- Vulnerability Scanning: Nessus  
- Monitoring: Zabbix  
- Antivirus: ClamAV / Windows Defender  
- Network Time: Chrony (NTP)

---

## 🧠 Key Features

- Network segmentation (Internal / DMZ / CDE / Attack / Backup)
- Centralized logging & SIEM monitoring
- File Integrity Monitoring (FIM)
- Active Response (automated blocking)
- Brute-force detection
- Privilege escalation monitoring
- LDAP & Active Directory integration
- Secure secret management with Vault
- WAF protection against web attacks
- Malware detection (ClamAV)
- Log retention aligned with PCI DSS

---

## 💳 Payment Application Security

A simulated payment system was implemented:

- Web server (Nginx + Reverse Proxy + WAF)
- Backend application (Python)
- Database (MariaDB)

Security controls:

- CVV is **never stored**
- PAN is **partially masked**
- Sensitive data is **encrypted via HashiCorp Vault**
- No hardcoded credentials (AppRole authentication)

---

## 🔍 Threat Detection (SOC Perspective)

Wazuh is used for centralized monitoring and detection:

- Authentication logs
- File changes (FIM)
- Brute-force attacks
- Suspicious command execution
- LDAP activity
- Malware-related file events

Custom rules were written to improve detection accuracy.

---

## 💣 Attack Simulation

Attacks were simulated from the Attack Zone:

- Brute-force attacks (Hydra)
- Suspicious file execution
- Unauthorized access attempts

All activities were monitored and detected via SIEM.

---

## 📊 Vulnerability Management

- Nessus scans performed on lab systems  
- High & Critical vulnerabilities identified  
- Remediation applied and re-tested  

---

## 📸 Screenshots & Diagrams

- Network topology → `/diagrams`
- Data flow diagrams → `/diagrams`
- Wazuh alerts → `/screenshots`
- Dashboard views → `/screenshots`

---

## 🧱 Security Approach

This lab follows a layered security model:

- Network segmentation  
- Least privilege access  
- Monitoring & alerting  
- Detection & response  
- Secure data handling  

---

## 🎯 Objective

The purpose of this lab is to:

- Simulate a real enterprise environment  
- Understand how attacks are detected  
- Build hands-on SOC & Security Engineering skills  

---

## 🧠 Key Takeaway

Building a system is easy.  
Securing and monitoring it is the real challenge.

---

## ⚠️ Disclaimer

This project is created for educational purposes only.
