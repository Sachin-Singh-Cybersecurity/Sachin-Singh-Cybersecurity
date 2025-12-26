# Day 11: Wireshark & Network Security Mechanisms (Dec 23, 2025)

## Topics Covered

### 1. Wireshark - Live Packet Capture & Analysis
- Wireshark installation on Kali Linux
- Interface: Packet List, Packet Details, Packet Bytes
- Display filters (dns, tcp.port == 80, ip.src, etc.)
- Real-time traffic analysis of lab network

### 2. DNS Packet Capture
- DNS query (CLIENT-01 → DC-01): "Where is dc01.contoso.local?"
- DNS response (DC-01 → CLIENT-01): "10.0.1.10"
- Transaction ID correlation
- UDP protocol (port 53, no reliability needed)

### 3. TCP Handshake Capture
- Three-way handshake: SYN → SYN-ACK → ACK
- Kerberos authentication on port 88
- Sequence number tracking
- Connection establishment verification

### 4. Firewalls: Stateless vs Stateful
- **Stateless:** Examines each packet independently
  - Fast but no context awareness
  - Can't detect SYN flood attacks
  - Simple rules: Allow/Deny based on IP/Port/Protocol

- **Stateful:** Maintains connection state table
  - Slower but intelligent decisions
  - Can detect anomalies and attacks
  - Context-aware: "Is this part of existing connection?"

### 5. Access Control Lists (ACLs)
- Detailed firewall rules
- Lab NSG: 
  - Allow: 53, 88, 389, 445 (AD services)
  - Block: Everything else
- Principle of least privilege

### 6. Network Address Translation (NAT)
- Translates private IPs to public IPs
- Hides internal network structure

### 7. VPN & Tunneling
- Encrypts traffic in tunnel
- Protects against MITM attacks
- Private tunnel through public internet

### 8. Data Loss Prevention (DLP)
- Blocks credit card numbers, passwords, documents
- Prevents accidental/intentional data exfiltration

## Lab Verification

### Allowed Ports (Verified via Nmap)
- Port 53 (DNS): OPEN ✅
- Port 88 (Kerberos): OPEN ✅
- Port 389 (LDAP): OPEN ✅
- Port 445 (SMB): OPEN ✅

### Blocked Ports (Verified via Nmap)
- Port 3389 (RDP): CLOSED ❌
- Port 4444 (Unknown): FILTERED ❌

### Wireshark Captures
- DNS resolution: dc01.contoso.local = 10.0.1.10 ✅
- Kerberos auth: TCP port 88 successful ✅
- TCP handshake: SYN-SYN-ACK-ACK verified ✅

## Key Concepts Understood

✅ Wireshark packet capture and analysis\
✅ TCP/IP layers visible in Wireshark\
✅ Stateless vs Stateful firewall differences\
✅ NSG configuration and rules\
✅ Network security mechanisms\
✅ Real-world attack patterns

## Next: Day 12 (Dec 24)

Topic: Cryptography Fundamentals
- Symmetric encryption (AES, DES)
- Asymmetric encryption (RSA, ECC)
- Hashing algorithms (SHA-256)
- Digital signatures
- SSL/TLS protocol
- Certificate management
- PKI architecture
