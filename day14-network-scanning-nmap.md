# Day 14: Network Scanning & Reconnaissance (Dec 27, 2025)

## Topics Covered

### 1. Reconnaissance Fundamentals
- **Passive Reconnaissance:** Public data, DNS, certificates (hard to detect)
- **Active Reconnaissance:** Port scanning, service enumeration (easy to detect)
- Three-phase attack: Reconnaissance → Exploitation → Post-Exploitation
- Defender and Penetration Tester both use same tools

### 2. Port Scanning Techniques
- **SYN Scan (-sS):** Half-open, stealthy, fast, DEFAULT
- **TCP Connect (-sT):** Full handshake, reliable, no privileges needed
- **UDP Scan (-sU):** Connectionless, finds UDP services
- Other scans: FIN, Null, Xmas (rarely used, easily detected)

### 3. Service Version Detection (-sV)
- Identifies services running on ports
- Determines version numbers
- Maps to known vulnerabilities
- Critical for targeting exploits

### 4. OS Fingerprinting (-O)
- Active fingerprinting using TCP/IP stack signatures
- Identifies Operating System
- Determines version (Windows Server 2022, Ubuntu 22.04, etc.)
- Accuracy: 95%+ with multiple open ports

### 5. NSE (Nmap Scripting Engine)
- Lua-based scripting for automation
- Vulnerability scanning scripts
- Service enumeration scripts
- Custom script capability

### 6. Lab Network Results
- DC-01: Windows Server 2022, Services: DNS, Kerberos, LDAP, SMB, SSH
- CLIENT-01: Windows 10, RDP
- UBUNTU-01: Ubuntu Linux, SSH
- Gateway: Router/Firewall

## Key Nmap Commands

```bash
# Host discovery (ping scan)
nmap -sn 10.0.1.0/24

# SYN scan (fast, default)
nmap -sS 10.0.1.10

# TCP connect scan (no privileges needed)
nmap -sT 10.0.1.10

# Service version detection
nmap -sV 10.0.1.10

# OS detection
nmap -O 10.0.1.10

# All-in-one aggressive scan
nmap -A 10.0.1.10

# SMB vulnerability scanning
nmap --script smb-vuln-* 10.0.1.10

# Specific ports
nmap -p 22,53,88,389,445 10.0.1.10

# All ports
nmap -p- 10.0.1.10

# Scan entire subnet
nmap -A 10.0.1.0/24
```

## Lab Verification

### Discovered Services
- Port 22: SSH (OpenSSH)
- Port 53: DNS (BIND)
- Port 88: Kerberos
- Port 389: LDAP
- Port 445: SMB (Samba)
- Port 3389: RDP (Windows)
  
### OS Detection
- DC-01: Windows Server 2022 ✅
- CLIENT-01: Windows 10 ✅
- UBUNTU-01: Ubuntu Linux 22.04 ✅
  
### Security Assessment
- Required ports open ✅
- Unnecessary ports filtered ✅
- Services versions identified ✅
- No critical vulnerabilities found ✅
  
### Key Concepts Understood
✅ Passive vs Active reconnaissance\
✅ SYN scan (stealthy, fast)\
✅ TCP connect scan (reliable)\
✅ UDP scan (connectionless)\
✅ Service version detection\
✅ OS fingerprinting\
✅ NSE vulnerability scanning\
✅ Network mapping and enumeration\
✅ Attacker methodology\
✅ Defender audit techniques

### Next: Day 15 (Dec 28)
Topic: Mini Project 1 - Network Assessment Report
- Comprehensive scan of lab network
- Document all findings
- Risk assessment
- Remediation recommendations
- Professional report format
