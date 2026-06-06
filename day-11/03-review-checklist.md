# Day 11 — Software & Information Security Review Checklist

## Mastery Checklist

### LO1: Malicious Code, Threats & Mitigation (4 items)
- [ ] **CIA Triad**: Confidentiality (unauthorized disclosure), Integrity (unauthorized modification), Availability (accessible when needed)
- [ ] **Non-repudiation**: cannot deny actions
- [ ] **Availability** is NOT controlled by cryptographic techniques
- [ ] **Risk** = overlap of threat (danger) + vulnerability (weakness)
- [ ] **Security Mechanisms**: detect, prevent, or recover from attacks
- [ ] Malware: Virus (host file), Worm (self-replicates network), Trojan (disguised), Ransomware (encrypts), Spyware (monitors), Adware (ads), Rootkit (OS-level hide)
- [ ] **Spam** = unsolicited commercial email
- [ ] NOT an IT security approach: **WannaCry** (ransomware attack)
- [ ] **Security estimation** = component of **Risk Management**
- [ ] Firewall: stops **unauthorized access**
- [ ] ACLs: **classify and organize** network traffic

### LO2: Cryptography
- [ ] **Symmetric** (same key): DES, 3DES, AES, Blowfish — fast, bulk data
- [ ] **Asymmetric** (key pair): RSA, ECC — slow, key exchange, signatures
- [ ] **DES**: 56-bit key, 64-bit blocks, **16 rounds**
- [ ] **3DES**: applies DES three times on 64-bit blocks with 56-bit keys
- [ ] **Combined Encryption**: symmetric key transmitted **asymmetrically**, message encrypted **symmetrically**
- [ ] **PKI**: sender signs with **sender's private key**; recipient decrypts with **recipient's private key**
- [ ] PKI decryption: recipient does NOT use sender's private key (obviously) or recipient's public key
- [ ] Hashing: MD5 (128-bit), SHA-1 (160-bit), SHA-256 — one-way, integrity

### LO3: Authentication & Access Control
- [ ] **Authentication** = who you are (identity verification)
- [ ] **Authorization** = what you can do (permission verification)
- [ ] Access control models: **DAC** (owner), **MAC** (clearance), **RBAC** (role)
- [ ] **OAuth**: Authorization Server validates identity
- [ ] **AAA**: Authentication, Authorization, Accounting

### LO4: Firewalls & Intrusion Detection
- [ ] Firewall types: packet-filtering, stateful, application-layer, next-gen
- [ ] **IDS**: passive, monitors, alerts
- [ ] **IPS**: inline, actively blocks
- [ ] Defense in depth: layered security approach

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| **CIA** | "**C**onfidentiality = **C**losed, **I**ntegrity = **I**ntact, **A**vailability = **A**ccessible" |
| **Risk formula** | "**R**isk = **T**hreat × **V**ulnerability" — RTV |
| **DES rounds** | "DES has **1****6** rounds — sweet sixteen" |
| **3DES** | "**3**DES = DES x **3** the work, same blocks" |
| **Symmetric vs Asymmetric** | "**S**ymmetric = **S**ame key; **A**symmetric = **A** pair of keys" |
| **PKI sign** | "Sign with **P**rivate = **P**rove it's you" |
| **PKI decrypt** | "**R**ecipient decrypts with **R**ecipient's **P**rivate" |
| **OAuth validator** | "**A**uthorization **S**erver = **A**uth **S**ervice" |
| **AuthN vs AuthZ** | "Auth**N** = **N**ame (who), Auth**Z** = **Z**one (what)" |
| **WannaCry** | "**W**annaCry = **W**annaCry (ransomware, not security tool)" |
| **IDS vs IPS** | "IDS = **D**etect (passive), IPS = **P**revent (active)" |
| **Availability** | "**A**vailability requires **A**lternatives (redundancy)" |

## 1-Page Cram Sheet

```
CIA TRIAD
═════════
Confidentiality → unauthorized disclosure ✗
Integrity       → unauthorized modification ✗
Availability    → accessible when needed (NOT crypto!)

CRYPTOGRAPHY
════════════
Symmetric (same key): DES, 3DES, AES, Blowfish
  DES: 56-bit key, 64-bit block, 16 rounds
  3DES: 3× DES on 64-bit blocks, 56-bit keys

Asymmetric (key pair): RSA, ECC

Combined Encryption:
  symmetric key → encrypted asymmetrically
  message → encrypted symmetrically

PKI:
  Sign/Authenticate → sender's PRIVATE key
  Verify signature  → sender's PUBLIC key
  Encrypt message   → recipient's PUBLIC key
  Decrypt message   → recipient's PRIVATE key

THREATS
═══════
Virus (host), Worm (network), Trojan (fake)
Ransomware (encrypt $), Spyware (monitor)
Adware (ads), Spam (email)

AUTHENTICATION vs AUTHORIZATION
═══════════════════════════════
Authentication  → who you are (identity)
Authorization   → what you can do (permission)

OAuth: Authorization Server validates user

ACCESS CONTROL: DAC (owner), MAC (clearance), RBAC (role)

AAA: Authentication, Authorization, Accounting

DEFENSE: Firewall (block), IDS (detect), IPS (prevent)
Security estimation → Risk Management component
```
