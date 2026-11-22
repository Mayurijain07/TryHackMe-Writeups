# 🎯 TryHackMe: Bounty Hacker

**Difficulty:** Easy  
**Category:** FTP Enumeration, SSH Brute-Forcing, Linux Privilege Escalation

## 📌 Room Overview

Bounty Hacker is a beginner-friendly Linux room focused on identifying exposed services, retrieving files through anonymous FTP access, discovering SSH credentials and escalating privileges through a misconfigured sudo permission.

The room demonstrates how multiple security weaknesses can be chained together to gain higher privileges.

## 🛠️ Tools Used

- Kali Linux
- Nmap
- Gobuster
- FTP
- Hydra
- SSH
- GTFOBins
- OpenVPN

## 🔍 1. Initial Reconnaissance

Connected to the TryHackMe lab network through OpenVPN and checked target connectivity.

```bash
ping <TARGET-IP>
```

Performed service and version detection:

```bash
nmap -sV -Pn -T4 <TARGET-IP>
```

**Learning:** Identified open ports and services to determine which services required further investigation.

## 🌐 2. Web Enumeration

Inspected the website source code using the browser:

```text
Ctrl + U
```

Used Gobuster to discover hidden directories and files:

```bash
gobuster dir -u http://<TARGET-IP> -w <WORDLIST>
```

**Learning:** Directory enumeration helps discover resources that are not directly linked from a website's homepage.

## 📁 3. FTP Enumeration

Connected to the FTP service:

```bash
ftp <TARGET-IP>
```

Tested anonymous access using:

```text
Username: anonymous
```

Listed available files and retrieved relevant files:

```bash
ls
get <FILENAME>
bye
```

Analysed the downloaded files for useful information, including possible usernames and credentials.

**Learning:** Anonymous FTP access can expose files without requiring authenticated access.

## 🔑 4. SSH Credential Testing Using Hydra

Used Hydra with a discovered username and a password wordlist to test SSH authentication.

```bash
hydra -l <USERNAME> -P <WORDLIST> <TARGET-IP> ssh
```

After identifying valid credentials, connected to the SSH service:

```bash
ssh <USERNAME>@<TARGET-IP>
```

**Learning:** Understood SSH authentication and how weak passwords can expose remote access.

## 🐧 5. Linux Privilege Escalation Discovery

After obtaining a normal user shell, checked the permitted elevated commands:

```bash
sudo -l
```

**Observation:** Identified a permitted `tar` command that could be executed with elevated privileges.

## 🔓 6. Privilege Escalation Using GTFOBins

Reviewed the permitted binary on GTFOBins to understand how the sudo configuration could be abused.

**Learning:** GTFOBins provides information about Unix binaries that can be used to bypass local security restrictions or escalate privileges when misconfigured.

The permitted `tar` command provided a path to higher privileges in the lab.

## 🧠 Key Concepts Learned

| Concept | Description |
|---|---|
| Anonymous FTP | FTP access without normal user authentication |
| Directory Enumeration | Discovering hidden web directories and files |
| Hydra | Tool used for login/password testing |
| SSH | Secure remote login protocol |
| Credential Reuse | Using credentials discovered through one service to access another |
| sudo -l | Displays commands a user is permitted to run through sudo |
| GTFOBins | Reference for Unix binaries that may be abused in security misconfigurations |
| Privilege Escalation | Moving from lower privileges to higher privileges |

## 🎯 Key Takeaways

- Practised Nmap service enumeration.
- Learned to inspect website source code.
- Used Gobuster for directory discovery.
- Identified anonymous FTP access and retrieved files.
- Practised SSH password testing with Hydra.
- Learned to inspect sudo permissions.
- Understood how an overly permissive sudo rule can lead to privilege escalation through GTFOBins.

---

**Lab Environment:** Kali Linux VM + VMware + OpenVPN  
**Purpose:** Educational cybersecurity lab practice.
