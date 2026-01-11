# Day 5 – Linux VMs in Azure (Dec 17, 2025)

## Azure Lab Topology (cybersec-lab)

VNet: cybersec-lab-vnet (10.0.0.0/16)
Subnet: cybersec-lab-subnet (10.0.1.0/24)

VMs:
- DC-01
  - OS: Windows Server 2022
  - Role: Domain Controller (contoso.local)
  - IP: 10.0.1.10

- CLIENT-01
  - OS: Windows 10
  - Role: Domain-joined client
  - IP: 10.0.1.20

- KALI-01
  - OS: Kali Linux (Azure marketplace)
  - Role: Attack box / pentesting
  - IP: 10.0.1.x (from DHCP – noted in lab)
  - Access: SSH from my IP

- UBUNTU-01
  - OS: Ubuntu Server 22.04
  - Role: Linux target / services box
  - IP: 10.0.1.x (from DHCP – noted in lab)
  - Access: SSH with key

Connectivity:
- All 4 VMs in same VNet + subnet
- KALI-01 and UBUNTU-01 can reach DC-01 and CLIENT-01 over VNet
