# 🛡️ Snort IDS Tutorial

Snort is a **free and open-source Intrusion Detection System (IDS)**.  
It analyzes network traffic in real time and detects suspicious or malicious activity using rule-based logic.  

This repository is a **student-friendly tutorial** that explains how to install, configure, and write custom rules in Snort.

---

## ⚙️ Installation

Install Snort on a Debian-based Linux distribution:

```bash
sudo apt-get install snort -y
```

Check if Snort is installed properly:

```bash
snort --version
```

During installation, when asked for an IP address range, enter:

```
192.168.0.0/24
```

---

## 🔧 Configuration

Edit the main Snort configuration file:

```bash
sudo nano /etc/snort/snort.conf
```

Find the line with `ipvar` and set:

```
ipvar HOME_NET 192.168.0.0/24
```

---

## 📜 Adding Rules

Open the **local rules file**:

```bash
sudo nano /etc/snort/rules/local.rules
```

Now add the following rules:

### Rule 1 – Detect ICMP Ping
```snort
alert icmp any any -> any any (msg:"ICMP Ping Detected"; sid:1000001; rev:1;)
```

### Rule 2 – Detect SSH Connection Attempts
```snort
alert tcp any any -> any 22 (msg:"SSH Connection Attempt"; sid:1000002; rev:1;)
```

### Rule 3 – Detect Nmap Scans
```snort
alert tcp any any -> any any (msg:"NMAP scan detected!"; sid:1000003; rev:1; priority:1;)
```

> ✅ Each rule has a unique **SID** (Snort ID). Avoid duplicates when creating custom rules.

---

## 📂 Logs

Snort logs alerts and activity in:

```bash
cat /var/log/snort/snort.log
```

---

## ✅ Summary

- Snort helps monitor and secure your network.  
- You can detect **ICMP pings, SSH attempts, and Nmap scans** with custom rules.  
- Logs provide detailed insights into detected activity.  

---

## 🏷️ Tags

`snort` · `ids` · `ips` · `cybersecurity` · `network-security` · `intrusion-detection` · `student-project` · `tutorial`

---

📘 This repository is intended as a **learning resource for students** exploring Snort IDS basics.
