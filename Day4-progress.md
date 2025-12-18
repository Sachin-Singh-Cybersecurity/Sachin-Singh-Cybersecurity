# Day 4: Windows 10 Client & Domain Integration

## Accomplishments

### Infrastructure Created
- CLIENT-01 VM deployed (Windows 10 Pro/Enterprise)
- Network configured (static IP: 10.0.1.20)
- DNS configured to use DC-01 (10.0.1.10)

### Domain Integration
- CLIENT-01 joined to contoso.local domain
- Domain join verified in AD
- Active Directory Users & Computers shows both DC-01 and CLIENT-01

### Test Users Created
1. jsmith (Sales Employee)
   - Password: *****
   
2. sjohnson (IT Employee)
   - Password: *****
   
3. mdavis (Manager)
   - Password: *****

### Testing Completed
- Domain user login successful
- whoami command verified domain context
- All users can login to domain

## Lab Status
Azure Infrastructure (cybersec-lab):\
├─ DC-01: ✅ Windows Server 2022, AD DC, Domain: contoso.local\
├─ CLIENT-01: ✅ Windows 10, Domain-joined, Can login with users\
├─ Network: ✅ Properly configured, VNet, Subnet, NSG\
└─ Test Users: ✅ 3 domain users created and tested

## Next Steps (Tomorrow)
- Deploy Linux VMs (Kali + Ubuntu)
- Configure network connectivity for all VMs
- Begin penetration testing scenarios
- Set up SIEM for log collection

## Time Investment
- Day 1: 4 hours
- Day 2: 9 hours
- Day 3: 4 hours
- Day 4: 4 hours
- **Total: 21 hours / 560 hours (3.75%)**
