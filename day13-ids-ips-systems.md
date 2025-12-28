# Day 13: IDS/IPS & Intrusion Detection Systems (Dec 26, 2025)

## Topics Covered

### 1. IDS vs IPS
- **IDS:** Intrusion Detection System (detects and alerts, passive)
- **IPS:** Intrusion Prevention System (detects, blocks, and alerts, active)
- Placement: IDS outside network, IPS inline
- Response: IDS manual, IPS automatic

### 2. HIDS vs NIDS
- **HIDS:** Host-based (runs on individual computers)
- **NIDS:** Network-based (runs on network appliance)
- Best practice: Use both for defense in depth

### 3. Detection Methods
- **Signature-Based:** Match known attack patterns
  - Fast, accurate for known attacks
  - Fails on zero-day vulnerabilities
  
- **Anomaly-Based:** Detect unusual behavior
  - Catches unknown attacks
  - High false positives possible
  
- **Hybrid:** Signature + Anomaly-based
  - Best detection coverage
  - Combines speed and future-proofing

### 4. Evasion Techniques
- Encoding/Obfuscation
- Encryption (HTTPS tunnels)
- Fragmentation (split payloads)
- Polymorphism (shape-shifting malware)
- Timing attacks (slow attacks over time)
- Flooding with noise
- Source spoofing
- IDS evasion tools (fragroute, Nikto)

### 5. Defense Against Evasion
- Hybrid detection (signature + anomaly)
- Deep packet inspection (decode, reassemble, normalize)
- Continuous signature updates
- Behavioral analytics
- Network segmentation
- Threat intelligence integration
- Incident response procedures

### 6. Snort
- Original open-source NIDS (since 1998)
- Rule-based signature detection
- Widely deployed in enterprise
- Can run as IDS or IPS

### 7. Suricata
- Modern NIDS/IPS alternative to Snort
- Multi-threaded (better performance)
- Advanced protocol analysis
- Compatible with Snort rules
- Growing adoption

## Lab Verification

### Detection Methods Tested
- Signature-based: Detecting known attack patterns ✅
- Anomaly-based: Detecting unusual behavior ✅
- Rule syntax: Understanding Snort/Suricata format ✅

### Tools Used
- Suricata: Open-source IDS/IPS
- Custom rules: Created detection rule ✅
- Alert generation: Triggered and verified ✅

## Key Concepts Understood

✅ IDS detects and alerts (passive)\
✅ IPS detects, blocks, and alerts (active)\
✅ Signature-based for known attacks\
✅ Anomaly-based for unknown threats\
✅ Hybrid approach best\
✅ Attackers use evasion techniques\
✅ Defense requires multiple strategies\
✅ Snort and Suricata tools

## Next: Day 14 (Dec 27)

Topic: Network Scanning & Reconnaissance (Nmap)
- Passive vs active scanning
- Nmap scanning types
- Service version detection
- OS fingerprinting
- Vulnerability scanning
