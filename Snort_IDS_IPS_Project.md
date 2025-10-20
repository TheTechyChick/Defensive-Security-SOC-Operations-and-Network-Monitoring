# Snort IDS/IPS Project

**Platform:** NetLab+ (CySA+ Virtual Lab)  
**Tools Used:** pfSense, Snort, Kali Linux, Ubuntu Server, MintOS  
**Environment Type:** Simulated corporate network (IDS/IPS deployment)

---

## 🎯 Objective
Deploy, configure, and test an intrusion detection and prevention system (IDS/IPS) using **Snort** on a pfSense firewall.  
This project demonstrates hands-on experience with rule management, alert analysis, and custom threat detection.

---

## 🧩 Key Activities

### 1. IDS/IPS Configuration
- Enabled Snort on pfSense WAN interface.  
- Applied **Emerging Threats Open** and **GPLv2 Community** rule sets.  
- Set rule update schedules and verified correct deployment.

### 2. Rule Activation and Analysis
- Activated multiple detection categories including **ET Open** and **AppID**.  
- Examined **GID/SID** identifiers and inspected rule syntax.  
- Observed alerts generated from simulated web application attacks.

### 3. Threat Simulation
- Deployed the vulnerable **BodgeIt web app** in a Docker container on Ubuntu.  
- Used **Kali Linux** to perform a **Cross-Site Scripting (XSS)** test.  
- Verified that Snort detected and logged the intrusion attempt.

### 4. Custom Rule Development
- Created a custom Snort rule to detect **TCP SYN flood** attacks.  
- Tested using `hping3` flood simulation.  
- Verified accurate detection and alerting.

---

## 📊 Outcomes and Skills Demonstrated
- Installed and configured Snort on pfSense.  
- Authored and tested custom IDS/IPS rules.  
- Simulated network attacks and analyzed Snort alerts.  
- Tuned rule thresholds for more precise detection.  
- Applied IDS/IPS knowledge for **SOC analysis** and **incident response** workflows.

---

## 🔧 Commands and Tools
- `sudo docker run -p 8080:8080 psiinon/bodgeit`  
- `sudo hping3 –c 15000 –d 120 –S –w 64 –p 3389 --flood --rand-source 203.0.113.1`  
- pfSense → *Services → Snort* (rule management GUI)

---

> **Lab-only example rule — do NOT run on production networks. Use only in an isolated lab environment.**
```snort
alert tcp any any -> 203.0.113.1 any (msg:"TCP SYN flood"; flow:stateless; flags:!A; detection_filter:track by_dst, count 70, seconds 10; sid:2000003;)


---

## 🧠 Reflection
This project builds real SOC-level experience with **Snort IDS/IPS**, including configuration, rule tuning, and alert validation.  
It demonstrates the ability to detect and prevent attacks through both **signature-based** and **custom rule** methods.

---

📄 *This project is an independent lab exercise based on personal study and practice. No proprietary NDG content is included.*
