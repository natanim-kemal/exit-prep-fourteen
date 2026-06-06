# Day 11 — Software & Information Security Trace Exercises & Problem-Solving (Exam-Style)

## Set 1: CIA Triad & Security Concepts

### Problem 1 — CIA Classification
Classify each scenario by which CIA objective is violated:
a) An employee reads the CEO's salary data → _________
b) A hacker modifies a student's grades → _________
c) A DDoS attack takes down an e-commerce site → _________
d) A customer denies placing an online order → _________

**Solution:**
a) **Confidentiality** — unauthorized disclosure
b) **Integrity** — unauthorized modification
c) **Availability** — system unavailable
d) **Non-repudiation** — denying action (not strictly CIA, but related)

---

### Problem 2 — Risk Formula
A server has a known vulnerability (unpatched OS). A hacker group is actively targeting similar servers. The overlap between the threat and the weakness creates what?

**Solution:** **Risk** — defined as the intersection of threat and vulnerability

---

### Problem 3 — Security Mechanisms
Match the security mechanism to its primary function:
1. Firewall → a. Detect/prevent unauthorized access
2. Encryption → b. Verify identity
3. Authentication → c. Protect data confidentiality
4. Hashing → d. Verify data integrity

**Solution:** 1-a, 2-c, 3-b, 4-d

---

## Set 2: Malware & Threats Trace

### Problem 4 — Malware Identification
Identify the malware type:
a) Self-replicates across network without a host file → _________
b) Disguised as a legitimate game, but steals passwords → _________
c) Encrypts all files and demands Bitcoin payment → _________
d) Unsolicited commercial email → _________
e) Displays pop-up ads without user consent → _________

**Solution:**
a) Worm
b) Trojan
c) Ransomware
d) Spam (not malware per se, but unwanted)
e) Adware

---

### Problem 5 — Threat vs Vulnerability
Classify each as threat, vulnerability, or risk:
a) A SQL injection flaw in the login code → _________
b) A hacker actively probing the network → _________
c) The combination of a hacker exploiting an unpatched server → _________

**Solution:**
a) Vulnerability (weakness in the code)
b) Threat (potential danger actor)
c) Risk (threat × vulnerability)

---

## Set 3: Cryptography Trace (Exam Priority)

### Problem 6 — Symmetric vs Asymmetric
Classify each algorithm:
a) DES → _________
b) RSA → _________
c) 3DES → _________
d) AES → _________
e) ECC → _________

**Solution:**
a) Symmetric
b) Asymmetric
c) Symmetric
d) Symmetric
e) Asymmetric

---

### Problem 7 — DES Details
How many rounds does DES use?
How many bits are in a DES key?
How many bits in a DES block?

**Solution:**
- **16 rounds**
- **56-bit key**
- **64-bit block**

---

### Problem 8 — Combined Encryption Trace
Alice wants to send a large encrypted file to Bob securely.

Step 1: Generate a random __________ key
Step 2: Encrypt the file with __________ key (fast)
Step 3: Encrypt the __________ key with Bob's __________ key
Step 4: Send encrypted file + encrypted __________ to Bob
Step 5: Bob decrypts the __________ key with his __________ key
Step 6: Bob decrypts the file with the __________ key

**Solution:**
Step 1: symmetric (secret)
Step 2: symmetric
Step 3: symmetric, public (asymmetric)
Step 4: symmetric key
Step 5: symmetric, private
Step 6: symmetric

---

### Problem 9 — PKI Key Usage
Fill in the correct key for each operation:

| Operation | Key Used |
|-----------|----------|
| Sender signs a document | Sender's ________ key |
| Recipient verifies signature | Sender's ________ key |
| Sender encrypts a message for recipient | Recipient's ________ key |
| Recipient decrypts the message | Recipient's ________ key |
| Authentication of sender | Sender's ________ key |
| Encryption of symmetric key in hybrid | Recipient's ________ key |

**Solution:**
- private (signing)
- public (verification)
- public (encryption)
- private (decryption)
- private (authentication = digital signature)
- public (hybrid encryption)

---

### Problem 10 — Triple DES
Which statement about Triple DES (3DES) is true?
a) Uses 192-bit keys on 64-bit blocks
b) Uses 128-bit blocks with 92-bit keys
c) Works with 192-bit blocks, applies DES once
d) **64-bit blocks, 56-bit keys, applies DES three times** ✓

**Solution:** d) — 3DES applies DES algorithm three times on 64-bit blocks with 56-bit keys (112-bit effective security with two keys, 168-bit with three keys)

---

## Set 4: Authentication & Access Control

### Problem 11 — AuthN vs AuthZ
At an airport:
a) Showing your passport at the counter → _________
b) The gate agent checks if you have a boarding pass for this flight → _________

**Solution:**
a) **Authentication** — proving who you are
b) **Authorization** — checking if you have permission to board

---

### Problem 12 — OAuth Flow Trace
Put these in order:
- [ ] Resource Server validates token
- [ ] Client redirects user to Authorization Server
- [ ] User authenticates
- [ ] Authorization Server issues token to Client
- [ ] Client accesses Resource Server with token

**Solution:**
1. Client redirects user to Authorization Server
2. User authenticates
3. Authorization Server issues token to Client
4. Client accesses Resource Server with token
5. Resource Server validates token

---

### Problem 13 — Access Control Identification
Which access control model fits each scenario?
a) A military system where clearance levels determine access → _________
b) A file's owner sets permissions for who can read/write → _________
c) An HR system where "Managers" role can view salaries → _________

**Solution:**
a) **MAC** (Mandatory Access Control — system-enforced, clearance-based)
b) **DAC** (Discretionary Access Control — owner sets permissions)
c) **RBAC** (Role-Based Access Control — permissions by role)

---

## Set 5: Firewalls & IDS

### Problem 14 — Firewall Purpose
A company deploys a firewall at the network perimeter. Which of the following is its primary function?
a) Scanning for viruses in email attachments
b) **Stopping unauthorized access by hackers**
c) Preventing physical fires from spreading
d) Encrypting all outbound traffic

**Solution:** b) Firewalls control access based on security rules

---

### Problem 15 — IDS vs IPS
Match:
1. IDS → a. Actively blocks malicious traffic inline
2. IPS → b. Passively monitors and alerts

**Solution:** 1-b, 2-a

---

### Problem 16 — Security Approach
Which is NOT a valid IT security approach?
a) Intrusion Detection System
b) **WannaCry protocol**
c) Physical security measures
d) Intrusion Prevention System

**Solution:** b) WannaCry is a ransomware attack, not a security approach

---

## Set 6: Security Architecture

### Problem 17 — Security in Architecture
"The system should use fine-grain, self-contained components. Producers of data separated from consumers. Shared data structures avoided." Which requirement is this for?
a) Availability
b) **Maintainability** ✓
c) Performance
d) Security

**Solution:** b) Maintainability — independent, self-contained components make the system easier to maintain

---

### Problem 18 — Risk Response
A security team finds a critical vulnerability. They decide to accept the risk and not fix it. This is:
a) Risk transfer
b) **Risk retention** ✓
c) Risk avoidance
d) Risk reduction

---

### Problem 19 — Security Estimation
Security estimation is a key component of which process?
a) SRS design
b) Software design
c) **Risk management** ✓
d) Software development

---

### Problem 20 — Multi-Layer Defense
An organization implements: firewall at perimeter, IDS on internal network, encrypted storage, and employee security training. What principle is being applied?

**Solution:** **Defense in depth** (layered security) — multiple layers of protection ensure that if one fails, others still provide coverage

---

## Common Exam Traps — Security

| Trap | Explanation |
|------|-------------|
| **Availability not crypto** | Availability is NOT controlled by cryptographic techniques (needs redundancy) |
| **Risk ≠ Vulnerability** | Risk = overlap of threat AND weakness (vulnerability alone is not risk) |
| **DES rounds** | DES has **16 rounds**, not 15 |
| **3DES block/key** | 3DES uses **64-bit blocks** with **56-bit keys**, applied three times |
| **RSA is asymmetric** | RSA is NOT symmetric — DES and 3DES are |
| **Combined encryption** | Secret key transmitted **asymmetrically**, message **symmetrically** |
| **PKI authentication** | Sender signs with **sender's private key** |
| **PKI decryption** | Recipient decrypts with **recipient's private key** |
| **OAuth validator** | **Authorization Server**, not Client or Resource Server |
| **Authorization ≠ AuthN** | Authorization = permission; Authentication = identity |
| **WannaCry** | NOT a security approach — it's a ransomware attack |
| **Spam = commercial** | Unsolicited commercial email = **spam**, not adware |
| **Security Mechanisms** | Detect, prevent, or **recover** from attacks |
| **Security Estimation** | Component of **Risk Management** |
| **Firewall purpose** | Stop **unauthorized access** |
