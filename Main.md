# 🛡️ Offensive Security & Penetration Testing Portfolio

<p align="center">
  <img src="https://img.shields.io/badge/Focus-Active%20Directory%20%26%20Web%20Pentesting-red?style=for-the-badge&logo=target" />
  <img src="https://img.shields.io/badge/Language-Bash%20%7C%20Python%20%7C%20PowerShell-blue?style=for-the-badge&logo=gnubash" />
  <img src="https://img.shields.io/badge/Status-In%20Progress-green?style=for-the-badge" />
</p>

---

## 👨‍💻 About This Repository
Welcome to my hands-on Cybersecurity Knowledge Base and Lab Notes! This repository contains my practical writeups, proof-of-concepts (PoCs), attack methodologies, and defensive mitigations across various penetration testing domains.

---

## 🗺️ Practical Syllabus & Progress Tracker

*(Note: Ticking `[x]` indicates lab completion and writeup upload.)*

### 🔍 01. RECONNAISSANCE
- [x] Passive Reconnaissance
- [x] Identifying Our Target & Scope
- [x] Discovering Email Addresses (`behindtheemail`)
- [x] Gathering Breached Credentials with `DeHashed`
- [x] Hunting Subdomains (`subdomain-finder`)
- [x] Identifying Website Technologies (`Wappalyzer`, `Netcraft`)
- [x] Google Dork (Advanced Search Operators)
- [x] Utilizing Social Media & OSINT Fundamentals

---

### 📡 02. Scanning & Enumeration
- [x] Network Scanning with `Nmap` (NSE Scripts & Port Auditing)
- [ ] Enumerating FTP (Port 21)
- [ ] Enumerating SNMP (Port 161/162)
- [ ] Enumerating HTTP and HTTPS (Port 80/443)
- [ ] Enumerating SMB (Port 139/445)
- [ ] Enumerating SSH (Port 22)
- [ ] Researching Potential Vulnerabilities & CVEs

---

### 🛡️ 03. Vulnerability Scanning with Nessus
- [ ] Installing & Configuring Nessus
- [ ] Performing Vulnerability Scans & Analyzing Reports

---

### 🎯 04. Exploitation Basics
- [ ] Understanding Reverse Shells vs Bind Shells
- [ ] Staged vs Non-Staged Payloads (`msfvenom`)
- [ ] Gaining Root/SYSTEM with Metasploit
- [ ] Manual Exploitation Walkthroughs
- [ ] Brute Force Attacks (`Hydra`)
- [ ] Credential Stuffing & Password Spraying

---

### 🏰 05. Active Directory Overview
- [ ] Active Directory Architecture & Fundamentals
- [ ] Physical Active Directory Components (Domain Controller, NTDS.dit)
- [ ] Logical Active Directory Components (Forests, Trees, Domains, OUs)

---

### ⚔️ 06. Attacking Active Directory: INITIAL ATTACK VECTORS
- [ ] LLMNR/NBT-NS Poisoning Overview
- [ ] Capturing Hashes with `Responder`
- [ ] Cracking Captured Hashes with `Hashcat` / `John`
- [ ] LLMNR Poisoning Mitigation & Hardening
- [ ] SMB Relay Attack Execution (`ntlmrelayx`)
- [ ] SMB Relay Attack Defenses (SMB Signing)
- [ ] Gaining Shell Access via Relaying
- [ ] IPv6 DNS Takeover via `mitm6`
- [ ] IPv6 Attack Defenses
- [ ] Passback Attacks (Printer/LDAP Exploitation)

---

### 🔎 07. Attacking Active Directory: POST-COMPROMISE ENUMERATION
- [ ] Domain Enumeration with `ldapdomaindump`
- [ ] Domain Enumeration & Attack Paths with `BloodHound`
- [ ] Domain Enumeration with `PlumHound`
- [ ] Active Directory Risk Assessment with `PingCastle`

---

### 💥 08. Attacking Active Directory: POST-COMPROMISE ATTACKS
- [ ] Pass Attacks Overview
- [ ] Dumping and Cracking Hashes
- [ ] Pass Attack Mitigations
- [ ] Kerberoasting Attack & Hash Extraction
- [ ] Kerberoasting Mitigation
- [ ] Token Impersonation Attack (`Incognito`)
- [ ] Token Impersonation Mitigation
- [ ] LNK File Attacks
- [ ] GPP / cPassword Attacks and Mitigations
- [ ] Credential Dumping with `Mimikatz` (LSASS Memory)
- [ ] DCSync Attack Execution
- [ ] Pass-the-Hash (PtH) Attack

---

### 👑 09. Domain Compromise & Persistence
- [ ] Dumping `NTDS.dit` (Extracting All Domain Hashes)
- [ ] Silver Ticket Attacks (Service Ticket Forgery)
- [ ] Golden Ticket Attacks (Full Domain Dominance)

---

### 🚨 10. Additional Active Directory Exploits
- [ ] Abusing ZeroLogon (`CVE-2020-1472`)
- [ ] PrintNightmare Exploitation (`CVE-2021-1675`)

---

### 🔄 11. Post Exploitation & Pivoting
- [ ] File Transfers Review (Linux/Windows Ingress & Egress)
- [ ] Maintaining Access & Persistence Overview
- [ ] Network Pivoting & Port Forwarding Overview
- [ ] Cleaning Up & Covering Tracks

---

### 🌐 12. Web Application Enumeration, Revisited
- [ ] Web Recon Introduction
- [ ] Installing & Setting up Go Environment
- [ ] Finding Subdomains with `Assetfinder`
- [ ] Finding Subdomains with `Amass`
- [ ] Finding Alive Domains with `Httprobe`
- [ ] Screenshotting Websites with `GoWitness`
- [ ] Automating the Reconnaissance Process (Bash Scripting)

---

### 🧪 13. Find & Exploit Common Web Vulnerabilities (OWASP)
- [ ] SQL Injection - Introduction
- [ ] SQL Injection - UNION Based
- [ ] SQL Injection - Blind (Time & Boolean)
- [ ] Cross-Site Scripting (XSS) - Introduction
- [ ] Cross-Site Scripting (XSS) - DOM Based
- [ ] Cross-Site Scripting (XSS) - Stored
- [ ] Command Injection - Basics
- [ ] Command Injection - Blind / Out-of-Band (OAST)
- [ ] Insecure File Upload - Introduction & Bypass
- [ ] Insecure File Upload - Basic Bypass
- [ ] Insecure File Upload - Magic Bytes Manipulation
- [ ] Attacking Authentication - Intro & Logic Flaws
- [ ] Attacking Authentication - Brute Force
- [ ] Attacking Authentication - MFA Bypass
- [ ] XML External Entity Injection (XXE)
- [ ] Insecure Direct Object Reference (IDOR)
- [ ] Capstone Lab - Full Web App Exploitation

---

### 📶 14. Wireless Penetration Testing
- [ ] Wireless Pentesting Overview & Fundamentals
- [ ] WPA/WPA2 PSK Exploit Walkthrough (4-Way Handshake Capture)

---

## 📁 Repository Directory Structure

```text
.
├── 01-Reconnaissance/
├── 02-Scanning-Enumeration/
├── 03-Vulnerability-Scanning/
├── 04-Exploitation-Basics/
├── 05-Active-Directory/
├── 06-Web-App-Security/
├── 07-Post-Exploitation/
└── 08-Wireless-Security/
