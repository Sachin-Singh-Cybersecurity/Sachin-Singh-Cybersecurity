# Day 12: Cryptography Fundamentals (Dec 24, 2025)

## Topics Covered

### 1. Symmetric Encryption
- **AES:** Modern standard (128/192/256-bit keys, 10-14 rounds)
  - Speed: Very fast (suitable for large data)
  - Security: No known practical attacks
  - Usage: HTTPS, full disk encryption, VPNs
- **DES:** Legacy/deprecated (56-bit key, 16 rounds)
  - Status: BROKEN (brute-forceable in seconds)
  - Never use for new systems

### 2. Asymmetric Encryption
- **RSA:** Most common public-key cryptography
  - Key sizes: 2048-bit (minimum), 4096-bit (recommended)
  - Security: Based on factoring problem
  - Usage: SSL/TLS certificates, SSH keys, code signing
  
- **ECC:** Modern alternative to RSA
  - Key sizes: 256-bit ≈ RSA-3072
  - Security: Based on discrete logarithm problem
  - Advantage: Smaller keys, faster computation
  - Usage: TLS 1.3, Bitcoin, SSH (ed25519)

### 3. Hashing Algorithms
- **MD5:** ❌ BROKEN (collisions found, never use)
- **SHA-1:** ❌ WEAK (being phased out)
- **SHA-256:** ✅ CURRENT STANDARD (256-bit output)
- **SHA-512:** ✅ MAXIMUM SECURITY (512-bit output)
- **SHA-3:** ✅ FUTURE STANDARD

### 4. Hashing Use Cases
- **Password Storage:** Hash with salt (use bcrypt/scrypt/Argon2)
- **Integrity Verification:** Verify file hasn't been modified
- **Digital Signatures:** Combined with asymmetric encryption

### 5. Digital Signatures
- **How they work:** Sign with private key, verify with public key
- **Proves:** Authentication (came from sender) + Integrity (not modified)
- **Legal:** Non-repudiation (can't deny sending)
- **Implementation:** Hash message, encrypt hash with private key

### 6. SSL/TLS Protocol
- **Purpose:** Secure tunnel for internet communication (HTTPS)
- **Handshake:** Negotiate encryption, authenticate server, exchange keys
- **TLS 1.2:** 2 round trips, good security
- **TLS 1.3:** 1 round trip, better security, faster
- **Session Key:** Symmetric AES-256 used for bulk data encryption

### 7. PKI (Public Key Infrastructure)
- **Certificate Authority (CA):** Verifies domain ownership, issues certificates
- **Certificate Chain:** End-entity → Intermediate → Root
- **Root Store:** Browser maintains list of ~100-150 trusted root CAs
- **Verification:** Browser checks certificate signature from trusted CA

## Lab Verification

### Cryptography in My Infrastructure
- **Kerberos:** Uses symmetric encryption (AES) for authentication
- **LDAP:** Can use TLS (LDAPS) for encrypted directory access
- **Domain Controller:** Has self-signed certificate for internal services
- **NSG:** Allows required ports (53 DNS, 88 Kerberos, 389 LDAP, 445 SMB)

## Key Concepts Understood

✅ Symmetric encryption (AES better than DES)\
✅ Asymmetric encryption (RSA and ECC)\
✅ Hashing (one-way function for integrity/passwords)\
✅ Digital signatures (authentication + integrity)\
✅ SSL/TLS handshake process\
✅ PKI and certificate chains\
✅ Real-world HTTPS security model

## Next: Day 13 (Dec 26)

Topic: Intrusion Detection & Prevention Systems
- IDS vs IPS concepts
- Signature-based and anomaly-based detection
- Network-based vs Host-based
- Evasion techniques
- Snort and Suricata tools
