# Day 10: Network Protocols & Security Fundamentals (Dec 22, 2025)

## Topics Covered

### 1. TCP/IP Model (4 Layers)
- **Application Layer:** HTTP, HTTPS, FTP, SSH, SMTP, DNS (ports 80, 443, 21, 22, 25, 53, etc.)
- **Transport Layer:** TCP (reliable), UDP (fast)
- **Internet Layer:** IP, ICMP, ARP (routing, diagnostics)
- **Data Link Layer:** Ethernet, MAC addressing (physical transmission)

### 2. Data Encapsulation
- Each layer adds its own header
- Messages → Segments → Packets → Frames
- Total overhead: ~74 bytes per 32 bytes data

### 3. TCP (Transmission Control Protocol)
- Reliable, ordered delivery
- Connection-oriented (3-way handshake)
- Flow control, error checking
- Used for: Web (HTTP), Email (SMTP), Remote access (SSH)
- Common attacks: SYN flood, RST attack, session hijacking

### 4. UDP (User Datagram Protocol)
- Fast, unreliable delivery
- Connectionless
- No flow control
- Used for: DNS, Video streaming, Online gaming
- Common attacks: UDP flood, amplification attacks

### 5. DNS (Domain Name System)
- Translates domain names to IP addresses
- Recursive query process: Root → TLD → Authoritative NS
- Your lab: DC-01 is authoritative for contoso.local
- Attacks: DNS spoofing, cache poisoning, enumeration
- Protection: DNSSEC, firewall rules, trusted servers

### 6. DHCP (Dynamic Host Configuration Protocol)
- Automatic IP address assignment
- DORA process: Discover → Offer → Request → Acknowledge
- Lease management (usually 24 hours)
- IP recycling when devices disconnect

### 7. Network Attacks & Vulnerabilities
- **DoS/DDoS:** Overwhelm service with traffic (SYN flood, UDP flood)
- **MITM:** Intercept & alter communication (ARP spoofing, DNS spoofing)
- **Protocol Exploitation:** Abuse specific weaknesses (IP fragmentation, sequence prediction)

### 8. Defense Mechanisms
- Firewalls: Block unnecessary ports
- Encryption: Prevent MITM attacks
- Authentication: Verify identities
- Monitoring: Detect anomalies
- Rate limiting: Prevent floods

## Lab Verification

### Verify DNS
CLIENT-01: nslookup dc01.contoso.local\
Result: 10.0.1.10 ✅

CLIENT-01: nslookup www.google.com \
Result: 142.250.185.14 (recursive query) 


### Verify Connectivity
KALI-01: ping 10.0.1.10\
Result: Responds ✅

KALI-01: nmap -p 53,88,389,445 10.0.1.10\
Result: AD services visible ✅

## Key Concepts Understood

✅ TCP/IP model and data flow\
✅ TCP vs UDP trade-offs\
✅ DNS resolution process\
✅ DHCP automatic configuration\
✅ Network attack vectors\
✅ Defense mechanisms

## Connection to Infrastructure

- DC-01 provides DNS for contoso.local
- VNet handles routing (like IP layer)
- NSG acts as firewall (layer 4 protection)
- Client-01 uses KERBEROS (TCP port 88)
- All communication on Azure backbone (encrypted by default)

## Next: Week 2 Day 11

Topic: Wireshark & Network Analysis
- Capture live traffic
- Analyze protocol interactions
- Detect anomalies
- Practice with your lab network
