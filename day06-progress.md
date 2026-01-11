# Day 6: Azure VNet Peering & Cross-Region Connectivity (Dec 18, 2025)

## Multi-Region Lab Architecture

### Resource Group: cybersec-lab (Single RG, multiple regions)

**East Asia Region:**
- VNet: cybersec-lab-vnet (10.0.0.0/16)
- Subnet: cybersec-lab-subnet (10.0.1.0/24)
- VMs:
  - DC-01 (10.0.1.10) - Windows Server 2022, Domain Controller
  - CLIENT-01 (10.0.1.20) - Windows 10, Domain-joined

**Central Indonesia Region:**
- VNet: linux-lab-vnet (10.1.0.0/29)
- Subnet: linux-lab-subnet (10.1.0.0/29)
- VMs:
  - KALI-01 (10.1.0.4) - Kali Linux, Attack box
  - UBUNTU-01 (10.1.0.5) - Ubuntu Server, Target/Testing

### VNet Peering: ✅ CONNECTED

**Peering Links Created:**
- cybersec-lab-vnet ↔ linux-lab-vnet (Global VNet Peering)
- Status: Connected
- Type: Global (cross-region)
- Cost: ~$0.02/GB inter-region data transfer

## Connectivity Testing Results

### Windows to Linux ✅
- DC-01 (10.0.1.10) → KALI-01 (10.1.0.4): ping successful
- CLIENT-01 (10.0.1.20) → UBUNTU-01 (10.1.0.5): ping successful

### Linux to Windows ✅
- KALI-01 (10.1.0.4) → DC-01 (10.0.1.10): ping successful
- UBUNTU-01 (10.1.0.5) → CLIENT-01 (10.0.1.20): ping successful

### Network Scanning ✅
- From KALI-01: nmap scan of DC-01 successful
- Detected: DNS (53), Kerberos (88), LDAP (389), SMB (445), RDP (3389)
- AD services visible across region boundary

### Traffic Path ✅
- All inter-region traffic flows through Azure backbone
- No public Internet exposure
- Low latency (typical: 50-100ms East Asia ↔ Central Indonesia)

## Lab Capabilities Unlocked

Now possible:\
✅ Penetration testing from KALI-01 against Windows network\
✅ Network reconnaissance across regions\
✅ Active Directory attack scenarios\
✅ Lateral movement practice\
✅ Incident response simulation\
✅ Multi-region security testing

## Cost Status

- Total monthly cost: ~$95 (4 B-series VMs)
- Inter-region peering: ~$0.02/GB (minimal for lab)
- Your cost: $0 (covered by $100 Azure student credits)

## Next Steps (Week 2)

- Deploy SIEM (Splunk/ELK) to collect logs from all 4 VMs
- Configure log shipping across regions
- Begin SOC threat detection scenarios
- Practice penetration testing (Week 3+)

## Course Progress

- Day 1: 4 hours (GitHub, CLI basics)
- Day 2: 9 hours (Fundamentals, case studies)
- Day 3: 4 hours (Azure setup, DC-01)
- Day 4: 4 hours (CLIENT-01, domain join)
- Day 5: 4 hours (Linux VMs in Azure)
- Day 6: 4 hours (VNet Peering, connectivity)

**Total: 29 hours / 560 hours (5.18%)**
