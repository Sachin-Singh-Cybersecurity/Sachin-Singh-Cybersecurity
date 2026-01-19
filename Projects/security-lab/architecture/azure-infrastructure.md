# Azure Lab Infrastructure

## VNet Topology
security-lab-vnet (10.0.0.0/16)\
├── management-subnet (10.0.1.0/24)\
├── windows-subnet (10.0.2.0/24)\
│ └── WinServer-Hardening (10.0.2.4)\
├── linux-subnet (10.0.3.0/24)\
│ └── Ubuntu-Hardening (10.0.3.4)\
└── monitoring-subnet (10.0.4.0/24) [Future]

## NSG Rules Applied
- Windows NSG: RDP 3389, SSH 22, HTTPS 443 (restricted)
- Linux NSG: SSH 22, HTTPS 443 (restricted)
- Default: Deny all inbound
