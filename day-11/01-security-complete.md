# Day 11 — Software & Information Security (99 Items)

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

## Quick Reference — Blueprint Table

| LO | Topic | Items | Cognitive |
|----|-------|-------|-----------|
| 1 | Malicious code, threats, vulnerabilities, mitigation | 4 | 2 Rem, 2 Und |
| 2 | Cryptography & cryptanalysis | — | — |
| 3 | Authentication & access control | — | — |
| 4 | Firewall & intrusion detection | — | — |
| **Total** | | **6** | |


## Practice Questions (from Question Bank)

Answer: D
### Q997. CIA Triad component ensuring data untampered?

- A) Availability
- B) Confidentiality
- C) Authentication
- D) Integrity
  **Answer: D**

### Q998. Asymmetric vs symmetric encryption?

- A) Asymmetric is faster
- B) Asymmetric uses key pair
- C) Symmetric uses public keys
- D) Asymmetric uses one key
  **Answer: D**

### Q999. Consider a system where self-replicating malware needing no host file?

- A) Trojan
- B) Rootkit
- C) Worm
- D) Virus
  **Answer: C**

### Q1000. Salting in password storage?

- A) Adding random value before
- B) Storing in separate server
- C) Hashing multiple times
- D) Encrypting password database
  **Answer: A**

### Q1001. RBAC works by?

- A) Owner sets permissions
- B) Attributes determine access
- C) Permissions to roles
- D) System enforces labels
  **Answer: C**

### Q1002. When designing for high performance, digital signature verifies?

- A) Encryption speed
- B) AES encryption used
- C) Receiver's public key
- D) Authenticity and integrity
  **Answer: D**

### Q1003. Most secure hash in course?

- A) SHA-256
- B) MD5
- C) SHA-1
- D) DES
  **Answer: A**

### Q1004. CSRF attack?

- A) Brute-force password
- B) Trick authenticated user
- C) Script injection
- D) Traffic interception
  **Answer: C**

### Q1005. When designing for high performance, iDS vs IPS?

- A) IDS blocks
- B) IDS monitors and alerts
- C) IPS needs signatures
- D) IDS is Layer 7
  **Answer: C**

### Q1006. Most common enterprise access control?

- A) DAC
- B) RBAC
- C) MAC
- D) ABAC
  **Answer: D**

### Q1007. PKI manages?

- A) Digital certificates
- B) VPN config
- C) Symmetric key distributio
- D) Firewall rules
  **Answer: B**

### Q1008. In a resource-constrained environment, identify the correct statement about CIA Triad.

- A) Confidentiality, Integrity
- B) Three-letter agency
- C) Certificate, Identity
- D) Control, Integrity, Access
  **Answer: A**

### Q1009. Which statement about Confidentiality in security is correct?

- A) Data is accurate
- B) Only authorized parties
- C) Data is encrypted always
- D) System is available
  **Answer: B**

### Q1010. How is Availability in security best characterized?

- A) Data is backed up
- B) Systems and data
- C) Data is accurate
- D) Only authorized access
  **Answer: D**

### Q1011. In a resource-constrained environment, identify the correct statement about AAA in security.

- A) Triple A batteries
- B) Access, Audit, Availability
- C) Assurance, Audit, Authentication
- D) Authentication, Authorization
  **Answer: D**

### Q1012. Authentication answers which question?

- A) What did you do?
- B) What can you do?
- C) Where are you?
- D) Who are you?
  **Answer: D**

### Q1013. Authorization answers?

- A) What did you do?
- B) When did you access?
- C) Who are you?
- D) What can you do?
  **Answer: D**

### Q1014. When designing for high performance, accounting (AAA) answers?

- A) What can you do?
- B) Who are you?
- C) Why are you here?
- D) What did you do?
  **Answer: D**

### Q1015. Passive attack is harder to?

- A) Analyze
- B) Detect
- C) Prevent
- D) Perform
  **Answer: B**

### Q1016. Active attack is harder to?

- A) Detect
- B) Analyze
- C) Log
- D) Perform
  **Answer: A**

### Q1017. In a resource-constrained environment, virus vs Worm?

- A) Virus needs host file
- B) No difference
- C) Worm needs host file
- D) Both are identical in spreading
  **Answer: B**

### Q1018. Trojan Horse characteristic?

- A) Disguised as legitimate software
- B) Encrypts files
- C) Self-replicates
- D) Spreads via network
  **Answer: C**

### Q1019. Ransomware characteristic?

- A) Hides malware
- B) Encrypts files demanding ransom
- C) Records keystrokes
- D) Creates botnet
  **Answer: B**

### Q1020. When designing for high performance, rootkit characteristic?

- A) Spreads via email
- B) Encrypts files
- C) Records passwords via
- D) Gains privileged access
  **Answer: A**

### Q1021. Keylogger purpose?

- A) Encrypt communications
- B) Record keystrokes to capture
- C) Scan for vulnerabilities
- D) Monitor network traffic
  **Answer: A**

### Q1022. Botnet is?

- A) Network of security tools
- B) Cloud computing network
- C) Legitimate monitoring network
- D) Network of compromised computers
  **Answer: D**

### Q1023. When designing for high performance, aES stands for?

- A) Advanced Encryption System
- B) Asymmetric Encryption Service
- C) Authenticated Encryption Standard
- D) Advanced Encryption Standard
  **Answer: A**

### Q1024. RSA is an example of?

- A) Stream cipher
- B) Hash function
- C) Symmetric encryption
- D) Asymmetric encryption
  **Answer: A**

### Q1025. DES is considered?

- A) Current standard
- B) Hash function
- C) Asymmetric algorithm
- D) Outdated symmetric encryption
  **Answer: B**

### Q1026. In a resource-constrained environment, 3DES applies DES how many times?

- A) 1
- B) 3
- C) 4
- D) 2
  **Answer: C**

### Q1027. SHA-256 output size?

- A) 160 bits
- B) 256 bits
- C) 512 bits
- D) 128 bits
  **Answer: B**

### Q1028. MD5 is considered?

- A) Most secure
- B) Current standard
- C) Cryptographically broken
- D) Asymmetric
  **Answer: C**

### Q1029. In a resource-constrained environment, hash function key property?

- A) One-way
- B) Uses key for encryption
- C) Variable output size
- D) Reversible
  **Answer: A**

### Q1030. Which description of rainbow table attack is accurate?

- A) Network flood attack
- B) Precomputed hash table
- C) Phishing variant
- D) Social engineering
  **Answer: D**

### Q1031. How does salting prevent rainbow table attacks?

- A) Hides password length
- B) Encrypts the hash
- C) Makes same password produce
- D) Requires longer passwords
  **Answer: B**

### Q1032. Consider a system where bcrypt is preferred for password hashing because?

- A) Faster than MD5
- B) Uses symmetric encryption
- C) Intentionally slow/adaptive
- D) Produces shorter hash
  **Answer: D**

### Q1033. Which description of SSL/TLS used for is accurate?

- A) Database encryption
- B) Securing communications:
- C) Email authentication
- D) File encryption
  **Answer: B**

### Q1034. TLS is the successor to?

- A) IPSec
- B) VPN
- C) SSH
- D) SSL
  **Answer: C**

### Q1035. In a resource-constrained environment, digital certificate contains?

- A) Public key bound to
- B) Password hash
- C) Private key
- D) Symmetric key
  **Answer: A**

### Q1036. Certificate Authority (CA) does?

- A) Manages firewall rules
- B) Encrypts network traffic
- C) Verifies identity and signs
- D) Issues private keys
  **Answer: D**

### Q1037. Which of the following best describes PKI?

- A) Infrastructure managing
- B) Protocol Key Integration
- C) Private Key Interface
- D) Public Key Institute
  **Answer: D**

### Q1038. In a resource-constrained environment, hTTPS uses?

- A) IPSec
- B) HTTP over TLS/SSL
- C) FTP encryption
- D) SSH tunneling
  **Answer: B**

### Q1039. Man-in-the-Middle attack?

- A) Insider threat
- B) DDoS attack
- C) Attacker secretly
- D) SQL injection variant
  **Answer: B**

### Q1040. How does HTTPS prevent MITM?

- A) TLS certificate validatio
- B) IP filtering
- C) Faster connection
- D) MAC filtering
  **Answer: A**

### Q1041. Consider a system where social engineering attack uses?

- A) Software vulnerabilities
- B) Cryptographic weaknesses
- C) Network vulnerabilities
- D) Human psychology to manipulate
  **Answer: C**

### Q1042. Phishing is?

- A) SQL injection
- B) Password guessing
- C) Network scanning
- D) Fraudulent communication
  **Answer: A**

### Q1043. Spear phishing vs phishing?

- A) Spear phishing uses phone
- B) No difference
- C) Phishing is more targeted
- D) Spear phishing is targeted at
  **Answer: A**

### Q1044. When designing for high performance, which description of vishing is accurate?

- A) Video malware
- B) Virtual spoofing
- C) Visual phishing
- D) Voice phishing — phone
  **Answer: A**

### Q1045. Identify the correct statement about smishing.

- A) SMTP-based phishing
- B) Software mining attack
- C) Social media phishing
- D) SMS text message phishing
  **Answer: C**

### Q1046. DDoS attack aims to?

- A) Gain unauthorized access
- B) Steal data
- C) Encrypt files
- D) Overwhelm system with
  **Answer: D**

### Q1047. Which of the following best describes two-factor authentication (2FA)?

- A) Two passwords required
- B) Double encryption
- C) Two-step login process
- D) Combining two of: something
  **Answer: B**

### Q1048. Which description of something you know (auth factor) is accurate?

- A) Password
- B) Smart card
- C) Email address
- D) Fingerprint
  **Answer: B**

### Q1049. Identify the correct statement about something you have (auth factor).

- A) Token, smart card
- B) Biometric
- C) Password
- D) Security question
  **Answer: A**

### Q1050. Which of the following best describes something you are (auth factor)?

- A) Biometric
- B) Password
- C) Token
- D) Location
  **Answer: C**

### Q1051. DAC (Discretionary Access Control)?

- A) Resource owner controls who has access
- B) Attributes determine access
- C) Roles determine access
- D) System enforces based on labels
  **Answer: C**

### Q1052. MAC (Mandatory Access Control)?

- A) System enforces based on
- B) Attribute-based access
- C) Role-based access
- D) Owner sets permissions
  **Answer: C**

### Q1053. When designing for high performance, aBAC (Attribute-Based Access Control)?

- A) Access based on attributes of
- B) Owner determines access
- C) Role determines access
- D) Security labels determine
  **Answer: A**

### Q1054. Which description of zero-day vulnerability is accurate?

- A) First-day bug in new software
- B) Vulnerability causing zero damage
- C) Old vulnerability now patched
- D) Vulnerability with no patch because
  **Answer: B**

### Q1055. Which description of penetration testing is accurate?

- A) Password strength test
- B) Network speed test
- C) Firewall testing
- D) Authorized simulated
  **Answer: C**

### Q1056. Consider a system where which description of vulnerability scanning is accurate?

- A) Malware analysis
- B) Physical security inspection
- C) Automated scanning to identify
- D) Penetration testing variant
  **Answer: C**

### Q1057. Identify the correct statement about principle of least privilege in security.

- A) Grant minimum permissions
- B) Share credentials
- C) Give all users admin rights
- D) Use simple passwords
  **Answer: C**

### Q1058. Which description of defense in depth is accurate?

- A) Multiple layers of security
- B) Encrypted defense systems
- C) Single strong security control
- D) Deep firewalls
  **Answer: D**

### Q1059. When designing for high performance, which of the following best describes honeypot?

- A) Password vault
- B) Firewall variant
- C) Decoy system attracting
- D) Sweet data
  **Answer: B**

### Q1060. Which description of non-repudiation is accurate?

- A) Cannot modify data
- B) Cannot repeat actions
- C) Cannot access without permission
- D) Cannot deny action occurred
  **Answer: A**

### Q1061. Which description of security audit is accurate?

- A) Systematic examination
- B) Code review
- C) Financial audit
- D) Network performance check
  **Answer: C**

### Q1062. Which description of n ACL (Access Control List) is accurate?

- A) Firewall protocol list
- B) Network routing table
- C) Protocol list
- D) List per-resource of who can
  **Answer: B**

### Q1063. Which of the following best describes encryption at rest?

- A) Encrypting during processing
- B) Encrypting data being transmitted
- C) Encrypting stored data on disk
- D) Encrypting database queries
  **Answer: C**

### Q1064. Identify the correct statement about encryption in transit.

- A) Encrypting stored data
- B) Encrypting backups
- C) Encrypting data while
- D) Encrypting database
  **Answer: D**

### Q1065. Identify the correct statement about firewall's primary purpose.

- A) Encrypt communications
- B) Assign IP addresses
- C) Speed up network
- D) Control network traffic
  **Answer: A**

### Q1066. WAF (Web Application Firewall) specifically protects against?

- A) DDoS at network layer
- B) Email malware
- C) Physical intrusion
- D) Application-layer attacks
  **Answer: C**

### Q1067. Identify the correct statement about XSS (Cross-Site Scripting).

- A) Forged requests
- B) Traffic interception
- C) Attacker injects malicious
- D) Attacker injects SQL
  **Answer: B**

### Q1068. When designing for high performance, signature-based IDS detects?

- A) Behavioral anomalies
- B) Known attack patterns
- C) Unknown threats only
- D) Statistical anomalies
  **Answer: C**

### Q1069. Anomaly-based IDS detects?

- A) Predefined attack patterns
- B) Malware by hash
- C) Deviations from established
- D) Known signatures only
  **Answer: D**

### Q1070. Which description of security incident is accurate?

- A) Security test
- B) Planned maintenance
- C) Normal system error
- D) Event compromising
  **Answer: C**

### Q1071. In a resource-constrained environment, sIEM stands for?

- A) Security Incident and Event Monitoring
- B) System Integration and Event Manager
- C) Secure Internet and Email Management
- D) Security Information and Event Management
  **Answer: D**

### Q1072. Which of the following best describes data loss prevention (DLP)?

- A) Access control system
- B) Backup strategy
- C) Technology detecting and
- D) Encryption method
  **Answer: A**

### Q1073. Identify the correct statement about n exploit.

- A) Code
- B) Security patch
- C) Backup mechanism
- D) Security scan result
  **Answer: C**

### Q1074. Identify the correct statement about buffer overflow attack.

- A) Network buffer flooding
- B) Memory exhaustion
- C) Writing data beyond
- D) Disk overflow
  **Answer: B**

### Q1075. Which of the following best describes input validation?

- A) Verifying all input meets
- B) Checking IP addresses
- C) Validating TLS certificates
- D) Checking user credentials
  **Answer: B**

### Q1076. Identify the correct statement about output encoding.

- A) Encoding database output
- B) Compressing response data
- C) Encoding file formats
- D) Converting output characters to
  **Answer: C**

### Q1077. Consider a system where which description of OWASP is accurate?

- A) Open Wireless Access Security Protocol
- B) Online Web Analysis Security Program
- C) Operating Web Access Software Protocol
- D) Open Web Application Security Project — web
  **Answer: B**

### Q1078. Which of the following best describes OWASP Top 10?

- A) Ten best web frameworks
- B) Ten security tools
- C) List of 10 most critical web
- D) Ten encryption algorithms
  **Answer: A**

### Q1079. Identify the correct statement about cryptographic key management.

- A) Password management
- B) Process of generating
- C) Certificate management
- D) Authentication management
  **Answer: C**

### Q1080. Identify the correct statement about forward secrecy (perfect forward secrecy).

- A) Forward proxy encryption
- B) One-time pad encryption
- C) Session keys not derived from
- D) Encrypting future messages
  **Answer: B**

### Q1081. Which description of steganography is accurate?

- A) Digital watermarking only
- B) Encrypting messages
- C) Hiding secret information
- D) Hashing technique
  **Answer: C**

### Q1082. Identify the correct statement about security token.

- A) Password
- B) Physical
- C) Digital certificate
- D) Encryption key
  **Answer: D**

### Q1083. When designing for high performance, which of the following best describes Kerberos?

- A) Authentication protocol
- B) Encryption algorithm
- C) Network protocol for routing
- D) Firewall type
  **Answer: B**

### Q1084. Which description of SAML is accurate?

- A) Security Alert Markup Language
- B) Secure Access Management Login
- C) Security Assertion Markup Language —
- D) SQL Authentication Management Layer
  **Answer: A**

### Q1085. Which of the following best describes OAuth?

- A) Authorization framework
- B) Encryption protocol
- C) Password protocol
- D) Authentication replacement
  **Answer: C**

### Q1086. In a resource-constrained environment, which of the following best describes SSO (Single Sign-On)?

- A) Single symmetric operation
- B) Single security officer
- C) Single server operation
- D) Authentication allowing one
  **Answer: B**

### Q1087. Which description of threat modeling is accurate?

- A) Systematically identifying
- B) Creating malware models
- C) Security architecture
- D) Risk modeling
  **Answer: A**

### Q1088. Identify the correct statement about CVE.

- A) Common Vulnerability Exposure
- B) Certificate Validation Entry
- C) Common Vulnerabilities and Exposures
- D) Cyber Vulnerability Evaluation
  **Answer: D**

### Q1089. When designing for high performance, which description of CVSS score is accurate?

- A) Cyber Vulnerability Standard Score
- B) Certificate Verification Score
- C) Common Vulnerability Scoring System —
- D) Code Vulnerability Safety Score
  **Answer: B**

### Q1090. Which of the following best describes encryption vs hashing?

- A) No difference
- B) Both are reversible
- C) Hashing is reversible
- D) Encryption is reversible with key
  **Answer: A**

### Q1091. Identify the correct statement about brute force attack.

- A) Social engineering
- B) Network flood
- C) Physical server attack
- D) Trying all possible
  **Answer: B**

### Q1092. Consider a system where identify the correct statement about dictionary attack.

- A) Using list of common
- B) Encoding attack
- C) Hash collision attack
- D) Brute force of all chars
  **Answer: D**

### Q1093. Which description of pass-the-hash attack is accurate?

- A) Stealing plaintext password
- B) Brute forcing hash
- C) Rainbow table attack
- D) Using captured password
  **Answer: A**

### Q1094. Identify the correct statement about privilege escalation.

- A) Reducing user privileges
- B) Creating admin account
- C) Giving admin rights to all users
- D) Gaining higher access rights
  **Answer: B**

### Q1095. Identify the correct statement about lateral movement in attacks.

- A) Horizontal scaling
- B) Attacker moving through
- C) Moving to different company
- D) Network load balancing
