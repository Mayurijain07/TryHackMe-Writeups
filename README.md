# 🔐 Cybersecurity Labs & Projects Portfolio

Welcome to my **Cybersecurity Journey Repository!**

This repository documents my hands-on cybersecurity practice, including TryHackMe labs, technical writeups, tools, commands and key learnings.

I am building my cybersecurity foundation through practical exercises in **penetration testing, system security, and ethical hacking**, while gradually focusing on **SOC Operations and Blue Team / Defensive Security**.

My goal is to strengthen my technical skills, understand attacker techniques and develop the knowledge required for a **SOC Analyst** role.

---

## 📌 Table of Contents

- [About Me](#-about-me)
- [Skills & Tools](#-skills--tools)
- [Labs & Projects](#-labs--projects)
  - [TryHackMe Labs](#-tryhackme-labs)
  - [Blue](#1-blue)
  - [Bounty Hacker](#2-bounty-hacker)
  - [Library](#3-library)
- [SOC & Blue Team Learning](#-soc--blue-team-learning)
- [How to Use This Repository](#-how-to-use-this-repository)
- [Future Plans](#-future-plans)

---

## 👩‍💻 About Me

I am a BCA student currently building my foundation in cybersecurity through structured learning and hands-on practice.

My current career goal is to become a **SOC Analyst**, with an interest in security monitoring, alert investigation, threat detection and incident response.

I also practise penetration testing labs to understand how vulnerabilities, misconfigurations and attacker techniques can affect systems.

**Currently Focusing On:**
- Cybersecurity Fundamentals
- SOC Operations & Blue Team Fundamentals
- Linux and Windows Security
- Network Reconnaissance & Enumeration
- Vulnerability Assessment
- Hands-on Security Labs

---

## 🛠️ Skills & Tools

*Growing list — updated as I gain more practical experience.*

### 🔍 Reconnaissance & Enumeration
- Nmap – Network scanning and service/version detection
- Gobuster – Web directory and file enumeration
- robots.txt – Discovering publicly exposed web paths
- Page Source Inspection – Identifying information exposed through website source code

### 🔐 Exploitation & Post-Exploitation
- Metasploit Framework – Exploit module configuration and execution
- Meterpreter – Post-exploitation session management
- MS17-010 / EternalBlue – Windows SMB vulnerability lab
- Hash Dumping – Understanding Windows credential hashes

### 🔑 Credential Attacks
- Hydra – SSH password brute-forcing
- RockYou Wordlist – Password dictionary testing
- FTP Anonymous Access – Identifying insecure FTP configurations

### 🐧 Linux Privilege Escalation
- sudo -l – Checking permitted elevated commands
- GTFOBins – Understanding privilege escalation through Unix binaries
- Python-based Privilege Escalation
- Misconfigured sudo permissions

### 💻 Operating Systems & Lab Environment
- Kali Linux
- Windows
- Linux
- Red Hat Enterprise Linux (RHEL)
- VMware
- OpenVPN

### 🧠 Core Concepts Practiced
- Network Reconnaissance
- FTP and SSH Authentication
- Remote Code Execution (RCE)
- Hashing: SHA-512 and NTLM
- Windows SAM Database
- Linux Privilege Escalation
- Authentication and Credential Security

---

## 📂 Labs & Projects

### 🔵 TryHackMe Labs

I have completed the following TryHackMe rooms as part of my practical cybersecurity learning journey.

All three rooms were completed using my own **Kali Linux virtual machine connected to the TryHackMe network through OpenVPN**, rather than the browser-based AttackBox.

| Room | Difficulty | Main Focus |
|---|---|---|
| [Blue](./blue/README.md) | Easy | Windows SMB Exploitation, Metasploit, Post-Exploitation |
| [Bounty Hacker](./bounty-hacker/README.md) | Easy | FTP Enumeration, SSH Brute-Forcing, Linux Privilege Escalation |
| [Library](./library/README.md) | Medium | Web Enumeration, SSH Brute-Forcing, Python Privilege Escalation |

### 1. Blue

<kbd>Easy</kbd> <kbd>Windows Exploitation</kbd> <kbd>Metasploit</kbd>

**Key Learning Areas:**
- Identifying open ports and services using Nmap
- Understanding the MS17-010 (EternalBlue) SMB vulnerability
- Exploitation using Metasploit Framework
- Obtaining an initial reverse shell
- Upgrading a shell to a Meterpreter session
- Understanding Windows hash dumping and SAM/NTLM

**Tools:** Nmap, Metasploit, Meterpreter, Kali Linux, OpenVPN

📖 [Read Complete Blue Writeup →](./blue/README.md)

---

### 2. Bounty Hacker

<kbd>Easy</kbd> <kbd>FTP Enumeration</kbd> <kbd>Linux Privilege Escalation</kbd>

**Key Learning Areas:**
- Network and service enumeration
- Inspecting website source code
- Discovering hidden directories using Gobuster
- Identifying anonymous FTP access
- Retrieving files from an FTP server
- SSH credential brute-forcing using Hydra
- Checking sudo permissions using `sudo -l`
- Understanding privilege escalation through GTFOBins

**Tools:** Nmap, Gobuster, Hydra, FTP, SSH, GTFOBins, Kali Linux

📖 [Read Complete Bounty Hacker Writeup →](./bounty-hacker/README.md)

---

### 3. Library

<kbd>Medium</kbd> <kbd>Web Enumeration</kbd> <kbd>Linux Privilege Escalation</kbd>

**Key Learning Areas:**
- Initial host and service enumeration
- Discovering exposed paths through robots.txt
- Website source inspection
- Directory enumeration using Gobuster
- Username discovery through web enumeration
- SSH password brute-forcing using Hydra and RockYou
- Analysing sudo permissions and wildcard rules
- Understanding Python-based privilege escalation
- Identifying the security risks of writable scripts executed with elevated privileges

**Tools:** Nmap, Gobuster, Hydra, RockYou Wordlist, SSH, Python, GTFOBins, Kali Linux

📖 [Read Complete Library Writeup →](./library/README.md)

---



## 📖 How to Use This Repository

Each TryHackMe room has its own folder containing a detailed `README.md`.

Every writeup documents:

- Room overview and objectives
- Difficulty and focus areas
- Tools and techniques used
- Step-by-step methodology
- Important commands and their purpose
- Troubleshooting and observations
- Key technical concepts
- Investigation takeaways

### Repository Structure

```text
TryHackMe-Writeups/
│
├── README.md
│
├── blue/
│   └── README.md
│
├── bounty-hacker/
│   └── README.md
│
└── library/
    └── README.md
```

**Note:** All writeups are documented for educational purposes. In accordance with TryHackMe guidelines, actual flag values are not published.

---



<p align="center">
  🌱 <i>Learning by doing, documenting every step, and growing one lab at a time.</i>
</p>

<p align="center">
  🔐 <b>Cybersecurity is a continuous learning journey!</b>
</p>
