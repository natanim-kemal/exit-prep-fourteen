# Day 11 — Software & Information Security Complete Theory (6 Items)

## LO1: Malicious Code, Threats, Vulnerabilities & Mitigation (4 items)

### 1.1 Security Terminology
| Term | Definition |
|------|------------|
| **Threat** | Potential danger to an asset (e.g., hacker, malware) |
| **Vulnerability** | Weakness in a system that can be exploited |
| **Risk** | The overlap of **threat** and an asset's **weakness** (vulnerability) |
| **Exploit** | Specific attack that takes advantage of a vulnerability |
| **Attack** | Actual attempt to destroy, expose, alter, or gain unauthorized access |

### 1.2 CIA Triad — Security Objectives
| Objective | Description |
|-----------|-------------|
| **Confidentiality** | Preventing **unauthorized disclosure** of information |
| **Integrity** | Preventing unauthorized modification; data accuracy and completeness |
| **Availability** | Ensuring information is accessible when needed |

**Non-repudiation**: ensuring someone cannot deny their actions (digital signatures)
- CIA + Non-repudiation = the core security objectives
- **Availability** is NOT controlled by cryptographic techniques alone (requires redundancy, backups)

### 1.3 Malware Types
| Type | Description |
|------|-------------|
| **Virus** | Attaches to programs; replicates when program runs |
| **Worm** | Self-replicates across networks without host file |
| **Trojan** | Disguised as legitimate software |
| **Ransomware** | Encrypts data and demands payment |
| **Spyware** | Secretly monitors user activity |
| **Adware** | Displays unwanted advertisements |
| **Rootkit** | Hides deep in OS for persistent access |
| **Spam** | Unsolicited commercial email (not technically malware) |

### 1.4 Security Mechanisms
- A process or device designed to **detect, prevent, or recover** from a security attack
- Examples: Firewalls, IDS, IPS, encryption, authentication

### 1.5 Mitigation Approaches
- **Use of Intrusion Detection System (IDS)** ✓
- **Use of Intrusion Prevention System (IPS)** ✓
- **Use of physical security** ✓
- **Use of Wana Cry protocol** ✗ — **NOT** an IT security approach (WannaCry is a ransomware attack)

### 1.6 Security Estimation
- Security estimation is an essential component of **Risk Management** process

### 1.7 Firewall
- **Purpose**: Stop **unauthorized access** by hackers
- Not for: virus scanning, fire prevention, or cable protection

---

## LO2: Cryptography & Cryptanalysis

### 2.1 Symmetric Encryption
- Same key for encryption and decryption
- **Fast**, suitable for bulk data
- Algorithms: **DES**, **3DES**, AES, Blowfish, RC4

**DES** (Data Encryption Standard):
- **56-bit** keys on **64-bit** blocks of plaintext
- Has initial and final permutation and **16 rounds**
- **3DES**: applies DES algorithm three times on 64-bit blocks with 56-bit keys (effective 168-bit or 112-bit security)

### 2.2 Asymmetric Encryption
- Public/private key pair
- **Slow**, used for key exchange, digital signatures
- Algorithms: **RSA**, ECC, Diffie-Hellman

### 2.3 Which algorithms belong to symmetric encryption?
- **DES** ✓ (symmetric)
- **3DES** ✓ (symmetric)
- **RSA** ✗ (asymmetric)
- "All except **a**" = DES, 3DES ✓

### 2.4 Combined Encryption (Hybrid)
```
Symmetric key encrypted asymmetrically → message encrypted symmetrically
```
1. Generate a random symmetric (secret) key
2. Encrypt the message with symmetric key (fast)
3. Encrypt only the symmetric key with recipient's public key (secure)
4. Send encrypted message + encrypted key

### 2.5 PKI (Public Key Infrastructure)
- **For authentication** (signing): **sender uses sender's private key** to sign
- **For decryption**: **recipient uses recipient's private key** to decrypt
- Keys NOT used for decryption by recipient: sender's private key, sender's public key

**PKI usage**:
| Operation | Key Used |
|-----------|----------|
| Sender authenticates/signs | Sender's **private** key |
| Recipient verifies signature | Sender's **public** key |
| Sender encrypts message | Recipient's **public** key |
| Recipient decrypts message | Recipient's **private** key |

### 2.6 Hashing
- One-way function: input → fixed-size hash
- MD5 (128-bit), SHA-1 (160-bit), SHA-256 (256-bit)
- Used for: password storage, integrity verification, digital signatures

---

## LO3: Authentication & Access Control

### 3.1 Authentication vs Authorization
| Concept | Description |
|---------|-------------|
| **Authentication** | Verifies **who you are** (identity) — login, password, biometric |
| **Authorization** | Verifies **what you can do** — permissions, access rights |

### 3.2 Access Control Models
| Model | Description |
|-------|-------------|
| **DAC** (Discretionary) | Owner controls access to their resources |
| **MAC** (Mandatory) | System-enforced based on clearance levels |
| **RBAC** (Role-Based) | Access based on user roles in the organization |

### 3.3 OAuth
- **Authorization Server**: validates the user's identity and issues tokens
- **Client**: application requesting access
- **Resource Server**: hosts protected resources
- **Not**: browser, client (doesn't validate), resource server

### 3.4 AAA
| Component | Description |
|-----------|-------------|
| **Authentication** | Who are you? |
| **Authorization** | What can you do? |
| **Accounting** | What did you do? (audit logs) |

---

## LO4: Firewalls & Intrusion Detection

### 4.1 Firewall Types
| Type | Description |
|------|-------------|
| **Packet-filtering** | Examines packet headers (IP, port) |
| **Stateful** | Tracks connection state |
| **Application-layer** | Inspects application data (proxy) |
| **Next-gen** | Combines firewall + IDS/IPS + application awareness |

### 4.2 IDS vs IPS
| Feature | IDS | IPS |
|---------|-----|-----|
| Full name | Intrusion **Detection** System | Intrusion **Prevention** System |
| Action | **Monitors and alerts** | **Blocks** attacks in real-time |
| Traffic | Passive (monitors copy) | Inline (passes through) |

### 4.3 ACLs (Access Control Lists)
- Benefits for security: **classify and organize network traffic**
- Not for: monitoring bytes/packets, virus detection, providing availability
- Sequential permit/deny rules, implicit deny at end

---

## Exam-Style Q&A (From 28 Actual Model Exam Questions)

**Q1:** Which security objective is NOT controlled by cryptographic techniques?
- a. Confidentiality
- b. Integrity
- c. Non-repudiation
- d. **Availability** ✓ (requires redundancy, backups — not crypto)

**Q2:** The overlap of threat and an asset's weakness is?
- a. Vulnerability
- b. Loss
- c. **Risk** ✓
- d. Exploit

**Q3:** Unsolicited commercial email is called?
- a. Virus
- b. **Spam** ✓
- c. Malware
- d. Adware

**Q4:** Which verifies whether you have permission to access specific resources?
- a. Authentication
- b. **Authorization** ✓
- c. Non-repudiation
- d. Accountability

**Q5:** A process designed to detect, prevent, or recover from a security attack?
- a. Security Attack
- b. Security Service
- c. Threat
- d. **Security Mechanisms** ✓

**Q6:** DES has an initial and final permutation and how many rounds?
- a. 15
- b. 14
- c. **16** ✓
- d. All

**Q7:** Which algorithms belong to symmetric encryption?
- a. RSA
- b. DES
- c. 3DES
- d. **All except a** ✓ (DES and 3DES are symmetric; RSA is asymmetric)

**Q8:** In Combined Encryption, how are keys used?
- a. **Secret key transmitted asymmetrically, message symmetrically** ✓
- b. Message encrypted symmetrically then asymmetrically
- c. Secret key transmitted symmetrically
- d. Message encrypted asymmetrically first

**Q9:** Which key does sender use for authentication in PKI?
- a. **Sender's private key** ✓
- b. Recipient's private key
- c. Sender's public key
- d. Recipient's public key

**Q10:** Which key is NOT used by recipient for decryption in PKI?
- a. Sender's private key ✓ (recipient never has sender's private key)
- b. Recipient's private key
- c. Sender's public key ✓ (used for verification, not decryption)
- d. Recipient's public key ✓ (used for encryption, not decryption)

**Q11:** Within OAuth, what validates the user's identity?
- a. Client
- b. **Authorization Server** ✓
- c. Resource Server
- d. Browser

**Q12:** Which refers to unauthorized disclosure of information?
- a. Authorization
- b. Authentication
- c. Integrity
- d. **Confidentiality** ✓

**Q13:** Triple DES functions on ___ blocks with ___ keys?
- a. 192-bit, 64-bit
- b. 128-bit, 92-bit
- c. 192-bit, applied once
- d. **64-bit blocks, 56-bit keys, applied three times** ✓

**Q14:** Which is NOT an approach used by IT security specialists?
- a. Use of IDS
- b. **Use of Wana cry protocol** ✓ (WannaCry is a ransomware attack, not a security approach)
- c. Use of physical security
- d. Use of IPS

**Q15:** Benefits of ACLs for security?
- a. Monitor bytes and packets
- b. Provide high availability
- c. Virus detection
- d. **Classify and organize network traffic** ✓

**Q16:** Security estimation is a component of which process?
- a. SRS design
- b. Software design
- c. **Risk management** ✓
- d. Software development

---

---

## Question Bank Study Notes

### CIA Triad
**Confidentiality** (encryption), **Integrity** (hashing), **Availability** (redundancy).

### Cryptography
Symmetric (AES — same key, fast): secures database storage. Asymmetric (RSA — public/private). Hashing (SHA-256): one-way. PKI: digital certificates for authentication.

### Threats
| Attack | Description | Defense |
|--------|------------|---------|
| Malware | Viruses, worms, Trojans, ransomware | Antivirus, patches |
| Phishing | Deceptive emails | User awareness |
| DoS/DDoS | Overwhelm server | Rate limiting |
| MitM | Intercept communication | TLS/SSL |
| SQL Injection | Inject malicious SQL | Prepared statements |
| XSS | Inject scripts | Output encoding, CSP |
| Session hijacking | Steal session cookies | HttpOnly, Secure flags |

Passive = monitor only (traffic analysis). Active = modify data (DoS, masquerade, replay).

### Malware Types
Virus (attaches to files), Worm (self-replicating), Trojan (disguised), Ransomware (encrypts + demands payment), Rootkit (hides in OS), Spyware (monitors), Adware (ads).

### Access Control
MFA (multi-factor): knowledge + possession + inherence. Firewalls: Packet Filtering, Stateful Inspection, Proxy, NGFW. IDS = monitor/alert. IPS = detect + block.

### Compliance
GDPR: users informed about data use. Least Privilege: minimum access. Defense in Depth: multiple security layers.


## Quick Reference — Blueprint Table

| LO | Topic | Items | Cognitive |
|----|-------|-------|-----------|
| 1 | Malicious code, threats, vulnerabilities, mitigation | 4 | 2 Rem, 2 Und |
| 2 | Cryptography & cryptanalysis | — | — |
| 3 | Authentication & access control | — | — |
| 4 | Firewall & intrusion detection | — | — |
| **Total** | | **6** | |
