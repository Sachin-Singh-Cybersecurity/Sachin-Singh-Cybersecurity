# Day 9: Phase 1 Deep Concept Mastery (Dec 21, 2025)

## Morning: Active Directory & Kerberos (4 hours)

### 1. What is Active Directory?
**Concept:** Centralized identity and access management  
**Problem Solved:** 5,000 employees, 2,000 computers  
**Without AD:** Manual management nightmare, inconsistent, insecure  
**With AD:** Centralized control, scalable, manageable

**Key Components:**
- Users (john.smith, etc.)
- Computers (CLIENT-01, DC-01)
- Groups (SalesUsers, ITUsers)
- Group Policies (password rules, software deployment)

**Real-World Impact:**
- Employee leaves: Disable one account → access revoked everywhere
- New software: Create GPO → auto-deployed to all machines
- Risk assessment: Audit logs show who accessed what, when

### 2. Kerberos Authentication: The Real Magic
**Problem:** How to authenticate securely without transmitting passwords

**Solution: Ticket-Based Authentication**
1. User logs in with password ONCE
2. DC-01 (KDC) issues Ticket Granting Ticket (TGT)
3. User uses TGT to get service tickets
4. User accesses resources WITHOUT re-entering password
5. Single Sign-On (SSO) achieved

**Security Advantages:**
- Password transmitted ONCE (during initial auth)
- Tickets used thereafter (safer, limited lifetime)
- Mutual authentication (both client and server prove identity)
- Timestamps prevent replay attacks
- Much faster than NTLM (legacy alternative)

**Attack Vectors Understood:**
- Kerberoasting: Crack service tickets offline
- Pass-the-Hash: Use NTLM hashes directly (Kerberos immune)
- Golden Tickets: If KRBTGT compromised, attacker creates forged tickets
- DCSync: If DC permissions wrong, attacker pulls all AD data

**Why DC-01 is Critical:**
- Authenticates every user
- Issues all tickets
- Stores all passwords (hashes)
- Manages all permissions
- MUST be protected above all else

### 3. My Lab Implementation
**What I built:**
- Domain: contoso.local
- DC: DC-01 (authentication authority)
- Client: CLIENT-01 (domain-joined, uses Kerberos)
- Users: jsmith, sjohnson, mdavis (test accounts)
- Groups: SalesUsers, ITUsers, etc.

**Security measures:**
- Strong password policy (12+ chars, complexity, 90-day expiry)
- Comprehensive audit logging (all authentications logged)
- Firewall rules (only required Kerberos ports open)
- Registry hardening (prevent exploitation)

## Evening: Linux Security & File Permissions (5 hours)

### 4. Linux Philosophy vs Windows
**Windows:** Trust by default
- Historically: Admin access by default
- Modern: UAC prompts for elevation
- Model: Allow exceptions

**Linux:** Deny by default
- Root is rare, users restricted
- Principle: Least Privilege
- Model: Grant only what's needed

**Implication:** Linux permissions = PRIMARY security control
- Every file protected by owner + group + permissions
- Even if program compromised, damage is limited
- Attacker confined to user's permissions

### 5. Unix Permission Model: Three Scopes
**Why three? Not just owner or everyone?**

Example: Shared project file
- Need: Owner can edit, developers can read, others blocked
- Solution: -rw-r----- (640)
  - Owner (alice): read+write (6)
  - Group (developers): read only (4)
  - Others: nothing (0)

**Why groups?**
- Scalability: Don't assign 5,000 individual permissions
- Create group: developers
- Assign permission to group once
- Add/remove developers → auto-get permissions

**Real-world use:**
- /etc/shadow (password hashes): 600 (only root reads)
- /var/www (websites): 755 (everyone reads, www-data writes)
- ~/.ssh/id_rsa (private key): 600 (only root access)

### 6. chmod Understanding
**Why chmod notation?**
- r (read) = 4
- w (write) = 2
- x (execute) = 1
- 755 = rwx r-x r-x = owner full, group read+execute, others read+execute

**Common examples:**
- 755: Programs (everyone can run, only owner modifies)
- 644: Data files (everyone reads, only owner modifies)
- 600: Secrets (only owner reads)

### 7. Attack Scenarios - What Happens When Permissions Break
**Scenario 1: Web server misconfiguration**
- Wrong: /etc/nginx/nginx.conf chmod 666
- Result: Attacker modifies config, redirects traffic
- Fix: chmod 644

**Scenario 2: SSH key theft**
- Wrong: ~/.ssh/id_rsa chmod 644
- Result: Attacker reads key, SSHs to servers
- Fix: chmod 600

**Scenario 3: Password file compromise**
- Wrong: /etc/shadow chmod 644
- Result: Attacker reads hashes, cracks passwords
- Fix: chmod 600

### 8. My Lab's Permission Strategy
**Day 8 Hardening Applied:**
sudo chmod 600 /etc/shadow # Only root sees passwords\
sudo chmod 600 /etc/ssh/sshd_config # Only root changes SSH settings\
sudo chmod 700 /etc/cron.d # Only root schedules tasks

text

**Result:** Principle of least privilege enforced
- If www-data compromised, cannot read passwords
- Damage contained to web application
- System remained protected

## Integration: Windows + Linux Security

**My Lab Architecture:**

Windows Domain (DC-01, CLIENT-01):
- Centralized authentication (Kerberos)
- Users login once, access everything
- Groups manage permissions at scale
- Audit logs everything

Linux Systems (UBUNTU-01, KALI-01):
- File permission-based security
- Least privilege by design
- Each process limited to user's permissions
- Damage contained if compromised

Combined Effect:
1. AD prevents unauthorized access\
2. Permissions contain damage if breached\
3. Audit logs detect attacks\
4. Defense in depth

## Course Progress

Morning (4 hours): Deep dive into AD concepts \ 
Evening (5 hours): Deep dive into Linux concepts  
**Day 9 Total: 9 hours**

**Course Total: 54.5 / 560 hours (9.73%)**

## Next Phase: Week 2

Ready to move into:
- Network Security Deep Dive (Dec 22-28)
- Wireshark analysis
- Network scanning
- Intrusion detection concepts
