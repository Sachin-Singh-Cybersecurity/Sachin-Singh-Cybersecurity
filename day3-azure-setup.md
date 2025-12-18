# Day 3 Progress - Azure Pivot & DC-01 Setup

## Overview
- Pivoted lab infrastructure from local VirtualBox to Microsoft Azure.
- Activated Azure for Students subscription with free credits.
- Deployed the first core server (DC-01) in Azure and promoted it to a Domain Controller for `contoso.local`.

## Azure Subscription & Access
- Activated **Azure for Students** account with $100 free credits (no credit card required).
- Verified access to **Azure Portal** at `https://portal.azure.com`.

## Resource Group & Networking
- Created **Resource Group**:
  - Name: `cybersec-lab`
  - Region: East Asia
- Created **Virtual Network**:
  - Name: `cybersec-lab-vnet`
  - Address space: `10.0.0.0/16`.
- Created **Subnet**:
  - Name: `cybersec-lab-subnet`
  - Address range: `10.0.1.0/24`.
- Created **Network Security Group**:
  - Name: `cybersec-lab-nsg`
  - Inbound rules:
    - Allow RDP (TCP 3389) from my IP.
    - Allow SSH (TCP 22) from my IP.
    - Allow ICMP (ping) for diagnostics.

## DC-01 (Windows Server 2022) VM
- Deployed **DC-01** virtual machine in Azure:
  - OS Image: Windows Server 2022 Datacenter.
  - Size: `Standard_B2s` (2 vCPU, 4 GB RAM).
  - Resource Group: `cybersec-lab`.
  - Network:
    - VNet: `cybersec-lab-vnet`.
    - Subnet: `cybersec-lab-subnet`.
    - NSG: `cybersec-lab-nsg`.
- Configured **static private IP** for DC-01:
  - IP address: `10.0.1.10`.

## Remote Access
- Connected to DC-01 using **RDP** via its public IP from Azure Portal.
- Verified:
  - Successful login with local admin (`azureadmin`).
  - Basic connectivity and server health.

## Active Directory Domain Services
- Installed **Active Directory Domain Services (AD DS)** and **DNS Server** roles via Server Manager on DC-01.
- Promoted DC-01 to a **Domain Controller**:
  - New forest: `contoso.local`.
  - Forest and domain functional level: Windows Server 2022.
  - DNS integrated with AD.
- After reboot, logged in as:
  - `contoso\azureadmin`.

## AD Verification
- Opened **Active Directory Users and Computers** on DC-01.
- Confirmed:
  - Domain `contoso.local` exists.
  - DC-01 appears under **Domain Controllers**.
  - Default containers:
    - `Built-in`
    - `Computers`
    - `Users`
- Verified DNS resolution for `contoso.local` on DC-01.

## Status Summary
- Azure student subscription: **ACTIVE**.
- Core lab network (RG, VNet, Subnet, NSG): **DEPLOYED**.
- Domain Controller (DC-01) with AD DS and DNS:
  - **ONLINE** and **FUNCTIONAL**.
- Domain `contoso.local`: **CREATED** and **VERIFIED**.

## Time & Progress
- Day 3 focused time: ~4 hours (Azure setup + DC-01 + AD promotion).
- Cumulative course time: **17 / 560 hours** (~3.0% complete).

## Next Steps
- Deploy Windows 10 client VM (**CLIENT-01**) in `cybersec-lab-vnet`.
- Configure CLIENT-01 networking (IP + DNS → DC-01).
- Join CLIENT-01 to `contoso.local` domain.
- Begin creating domain user accounts for testing.
