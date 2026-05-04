# 🛡️ Enterprise Security Lab (PCI DSS Inspired)

> A hands-on cybersecurity lab simulating a real-world enterprise environment with secure architecture, monitoring, detection, and response capabilities.

---

## 🔍 Overview

This project demonstrates a full enterprise-grade security lab designed based on PCI DSS principles.

The environment simulates a real-world infrastructure including:

- Segmented network architecture (Internal, DMZ, CDE, Attack, Backup)
- Centralized monitoring & detection (Wazuh SIEM)
- Secure payment application with encrypted data storage
- Identity & access management (Active Directory, LDAP)
- Network security controls (Firewall, IDS/IPS, WAF)
- Vulnerability management and remediation lifecycle

The goal is not just building systems, but securing, monitoring, and validating them against real attack scenarios.

---

## 🗺️ Network Architecture

![Topology](./diagrams/topology.png)

### Zones

- **Internal Zone** → Active Directory, user machines
- **DMZ Zone** → Wazuh, Web Server, Jump Server, Vault, LDAP
- **CDE Zone** → Application server & Database (Cardholder data)
- **Attack Zone** → Kali Linux, Metasploitable
- **Backup Zone** → Backup server

All traffic is controlled through **pfSense firewall** with a default deny approach.

---

## 🔧 Technologies & Purpose

- **Wazuh** → SIEM + log correlation + detection
- **pfSense** → Network segmentation & firewall enforcement
- **Suricata** → IDS/IPS (network-level threat detection)
- **ModSecurity (WAF)** → Protection against web attacks (SQLi, XSS)
- **Active Directory** → Centralized identity management
- **LDAP** → Authentication & directory services
- **HashiCorp Vault** → Secret management & data encryption
- **Nessus** → Vulnerability scanning & risk analysis
- **ClamAV** → Malware detection
- **Chrony (NTP)** → Time synchronization across systems

---

## 💳 Secure Payment Application

- Payment form served via **Nginx (Reverse Proxy + WAF)**
- Sensitive data handling:
  - CVV is **never stored**
  - PAN is **masked (truncated)**
  - Data is encrypted before database insertion
- Encryption:
  - Managed via **HashiCorp Vault**
  - AppRole-based authentication (no hardcoded secrets)
- Database:
  - MariaDB with encrypted records

---

## 🛡️ Security Controls

- Network segmentation (multi-zone architecture)
- Firewall rules (default deny)
- IDS/IPS (Suricata inline mode)
- Web Application Firewall (ModSecurity)
- VPN access (OpenVPN)
- MFA for privileged access
- SSH hardening & RDP restrictions
- Centralized time sync (NTP)
- Endpoint protection (ClamAV / Windows Defender)

---

## 📡 Monitoring & Detection (SOC Perspective)

- Centralized logging via **Wazuh SIEM**
- File Integrity Monitoring (FIM)
- Brute-force detection
- LDAP user activity monitoring
- Root/admin activity tracking
- WAF log analysis
- Malware detection alerts
- Active response (automatic blocking)

---

## 🧪 Attack & Detection Scenario

### Scenario:
An attacker from the **Attack Zone (Kali Linux)** performs brute-force and enumeration attempts against internal systems.

### Detection:
- Wazuh detects multiple failed login attempts
- Alerts generated with high severity
- Logs correlated across endpoints

### Response:
- Active response blocks attacker IP
- Firewall rules updated dynamically
- Alert notification sent (email)

### Remediation:
- Password policies enforced
- Services hardened
- Attack surface reduced

---

## 🔍 Vulnerability Management

- Scanning performed using **Nessus**
- Focus on **High & Critical vulnerabilities**
- Manual analysis of findings
- Remediation applied
- Re-scan to verify fixes

---

## 📊 Outcomes

- Successfully detected brute-force and unauthorized access attempts
- Built centralized monitoring across all systems
- Implemented secure data handling practices
- Reduced attack surface via segmentation and hardening
- Simulated real-world SOC monitoring workflow

---

## 📌 PCI DSS Alignment

- **Requirement 1** → Firewall configuration (pfSense)
- **Requirement 3** → Data protection (Vault encryption)
- **Requirement 10** → Logging & monitoring (Wazuh)
- **Requirement 11** → Vulnerability scanning (Nessus)

---

## 📸 Screenshots

### Wazuh Alert Example
![Alert](./screenshots/wazuh-alert.png)

### Wazuh Dashboard
![Dashboard](./screenshots/wazuh-dashboard.png)

---

## 🎯 Key Takeaways

- Building systems is easy — securing and monitoring them is the real challenge
- Visibility is critical in cybersecurity
- Defense-in-depth is essential
- Detection & response are as important as prevention

---

## 🚀 Future Improvements

- SOAR integration (automated response workflows)
- Threat intelligence feeds integration
- Advanced detection rules (custom correlation)
- Cloud environment extension (AWS/Azure)

---

## 👤 Author

**Muhammet Emin Okten**

Cybersecurity enthusiast focused on Security Engineering & SOC operations.
