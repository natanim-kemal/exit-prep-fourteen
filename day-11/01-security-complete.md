# Software & Information Security — Study Notes

## 1. Security Goals (CIA Triad)

- **Confidentiality**: data accessible only to authorized parties (encryption, access control)
- **Integrity**: data is accurate and unaltered (hashing, digital signatures)
- **Availability**: data accessible when needed (redundancy, backups, DDoS protection)

## 2. Cryptography

**Core objectives**:
- **Confidentiality**: encryption keeps data secret
- **Integrity**: detect tampering (hashing, MAC)
- **Authentication**: verify identity of communicating parties
- **Non-repudiation**: sender cannot deny sending (digital signatures)

**Encryption types**:
- **Symmetric**: same key for encryption/decryption (AES, DES, 3DES) — fast, but key distribution problem
- **Asymmetric**: public/private key pair (RSA, ECC) — slower, but solves key distribution
- **AES (Advanced Encryption Standard)**: used to secure database storage
- **Hashing**: one-way function (SHA-256, MD5) — integrity verification, password storage
- **Digital signatures**: authenticate sender and ensure non-repudiation

**PKI (Public Key Infrastructure)**: manages digital certificates for secure authentication using cryptographic certificates.

## 3. Network Threats & Attacks

| Attack | Description | Countermeasure |
|--------|------------|--------------|
| **Malware** | Viruses, worms, Trojans, ransomware | Antivirus, patches |
| **Phishing** | Social engineering via deceptive emails | User awareness, email filtering |
| **DoS/DDoS** | Overwhelm server with traffic | Rate limiting, DDoS protection |
| **Man-in-the-Middle (MitM)** | Intercept communication | TLS/SSL encryption |
| **SQL Injection** | Inject malicious SQL | Prepared statements |
| **XSS** | Inject malicious scripts | Output encoding, CSP |
| **Session hijacking** | Steal session cookies | HttpOnly, Secure flags, session timeout |

**Passive attacks**: monitoring/traffic analysis (eavesdropping, packet sniffing) — does NOT modify data.
**Active attacks**: modification, masquerade, replay, DoS — modifies data or disrupts service.

## 4. Malware Types

| Type | Description |
|------|------------|
| **Virus** | Attaches to legitimate files; requires host to spread |
| **Worm** | Self-replicating; spreads without host |
| **Trojan** | Disguised as legitimate software |
| **Ransomware** | Encrypts files and demands payment for decryption |
| **Rootkit** | Hides deep in OS; provides privileged access |
| **Spyware** | Secretly monitors user activity |
| **Adware** | Displays unwanted advertisements |

## 5. Access Control

**Authentication methods**:
- **Something you know**: password, PIN
- **Something you have**: token, smart card, OTP
- **Something you are**: biometric (fingerprint, face, iris)
- **Multi-Factor Authentication (MFA)**: combines two+ methods

**Authorization models**: DAC (Discretionary), MAC (Mandatory), RBAC (Role-Based), ABAC (Attribute-Based).

## 6. Firewalls & IDS

**Firewall types**:
- **Packet Filtering**: checks packet headers (IP, port) — simple
- **Stateful Inspection**: tracks connection state — allows only legitimate traffic in established connections
- **Proxy Firewall**: acts as intermediary between client and server (deep inspection)
- **Next-Gen Firewall (NGFW)**: application-aware, integrated IDS/IPS

**IDS (Intrusion Detection System)**: monitors and alerts on suspicious activity.
**IPS (Intrusion Prevention System)**: detects AND blocks threats in real-time.

## 7. Security Policies & Compliance

- **GDPR (General Data Protection Regulation)**: EU privacy law — users must be informed about how their data is used
- **CCPA**: California Consumer Privacy Act
- **ISO 27001**: international standard for information security management
- **Principle of Least Privilege**: users get minimum access needed
- **Defense in Depth**: multiple layers of security controls

## 8. Application Security

- **Secure coding**: input validation, output encoding, parameterized queries
- **OWASP Top 10**: most critical web application security risks
- **Security testing**: SAST (static), DAST (dynamic), penetration testing
- **Vulnerability assessment**: identify, classify, prioritize vulnerabilities
