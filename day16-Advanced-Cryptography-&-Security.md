# Day 16 – Advanced Cryptography (December 29, 2025)

**Week:** 3 · **Day:** 16  
**Focus:** Advanced Cryptography & Security  
**Total Time:** 4 hours  

---

## Overview

- Deep dive into modern cryptography in practice  
- Why many legacy algorithms and modes are unsafe  
- How passwords should be stored securely  
- How real-world crypto failures lead to breaches  

---

## Topics Studied

### Cryptographic Weaknesses

- Broken or outdated algorithms (DES, MD5, SHA‑1) and why they are deprecated.  
- Typical implementation mistakes: bad randomness, key reuse, weak keys, roll‑your‑own crypto.  
- Examples of historic protocol failures (e.g. WEP, early SSL/TLS issues).

### Key Management Basics

- Key lifecycle: generation → storage → rotation → revocation → destruction.  
- Secure generation with CSPRNGs vs insecure sources (e.g. `Math.random`).  
- Storage approaches: HSM/KMS, environment secrets, never hard‑coding in code or git.  
- Importance of periodic key rotation and immediate revocation on compromise.

### Cipher Modes in Practice

- ECB: deterministic per block, leaks patterns, never use.  
- CBC: hides patterns but no integrity and needs IV management.  
- GCM: AEAD mode providing confidentiality + integrity + authenticity.  
- Why modern TLS ciphersuites prefer AES‑GCM and ChaCha20‑Poly1305.

### Password Storage & Hashing

- Why plain MD5/SHA‑1/SHA‑256 are unsafe for passwords (too fast, rainbow tables).  
- Salt: unique, random per user; defeats rainbow tables and makes precomputation useless.  
- Slow, adaptive password hashing:
  - `bcrypt` with cost factor.
  - `scrypt` and `argon2` (memory‑hard, GPU‑resistant).
- Tradeoff: ~100–200 ms per password hash is desirable for login.

### Diffie–Hellman & Forward Secrecy (conceptual link)

- High‑level idea of secure key exchange over an insecure channel.  
- Concept of Perfect Forward Secrecy via ephemeral key exchanges (ECDHE).  
- Why PFS protects *past* sessions even if long‑term keys are later compromised.

---

## Hands‑On Work

### Lab 1 – Hash Cracking & Rainbow Tables

- Took a small set of common passwords and their MD5 hashes.  
- Used online rainbow‑table style lookup to “crack” the hashes instantly.  
- Observed:
  - Unsalted MD5 hashes are trivial to reverse.
  - Same password → same hash across all users → huge risk.  
- Demonstrated how adding a unique salt per user completely breaks the effectiveness of rainbow tables.

### Lab 2 – Block Cipher Modes

- Compared how the same repeated plaintext blocks behave under:
  - ECB: identical ciphertext blocks, pattern leakage (classic “ECB penguin” effect).  
  - CBC: each block chained from previous ciphertext, patterns no longer visible.  
  - GCM: modern AEAD mode including an authentication tag.  
- Understood why:
  - ECB must never be used for anything sensitive.
  - GCM (or similar AEAD) is preferred for modern protocols like TLS 1.3.

### Lab 3 – Password Hash Algorithm Benchmarks

- Conceptually measured relative speeds:
  - MD5 / SHA‑256: extremely fast → great for integrity, terrible for passwords.  
  - `bcrypt`/`scrypt`/`argon2`: intentionally slow and/or memory‑hard.  
- Saw how increasing cost/iterations slows brute force from seconds to hours/days.  
- Mapped algorithms to correct use cases:
  - Passwords → `bcrypt` or `argon2`.  
  - File integrity / checksums → SHA‑256.  

### Lab 4 – Real‑World Crypto Failures

- WEP:
  - Reused short IVs and weak design → practical attacks in minutes.  
- DES:
  - 56‑bit key → brute‑forced with dedicated hardware → replaced by AES.  
- Insecure RNG:
  - Using non‑crypto RNGs for keys/IVs makes systems predictable and breakable.  

---

## Key Learnings – Day 16

- Never use legacy primitives like DES, RC4, MD5, SHA‑1 in new designs.  
- Always combine **salt + slow, adaptive hash** for password storage.  
- Avoid ECB entirely; prefer AEAD modes like **AES‑GCM**.  
- Crypto is easy to misuse – rely on well‑tested libraries and standard protocols.  
- Good key management and PFS matter as much as algorithm choice.
