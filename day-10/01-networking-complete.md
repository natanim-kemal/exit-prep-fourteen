# Day 10 — Fundamentals of Networking Complete Theory (8 Items)

## LO1: Network Fundamentals (2 items)

### 1.1 What is a Network?
- Interconnected collection of computers and devices for data sharing
- **LAN**: Local Area Network (small area, e.g., office)
- **WAN**: Wide Area Network (large geographic, e.g., the Internet)
- **MAN**: Metropolitan Area Network (city-wide)
- **PAN**: Personal Area Network (personal devices)

### 1.2 Network Topologies
| Topology | Description | Pros | Cons |
|----------|-------------|------|------|
| **Bus** | Single cable, all nodes connect | Simple, cheap | Single point of failure, limited distance |
| **Star** | All nodes connect to central hub/switch | Easy to manage, fault isolation | Hub failure = entire network down |
| **Ring** | Each node connects to two neighbors | Orderly data flow | Single break affects all |
| **Mesh** | Every node connects to every other | Highly redundant, fault-tolerant | Expensive, complex wiring |
| **Tree** | Hierarchical star topology | Scalable | Root failure = large impact |

### 1.3 Network Devices (Exam Priority)
| Device | Layer | Function |
|--------|-------|----------|
| **Repeater** | Physical (L1) | Regenerates signal, extends distance |
| **Hub** | Physical (L1) | Connects devices, broadcasts to all ports, **cannot filter frames** |
| **Bridge** | Data Link (L2) | Connects two segments, filters by MAC |
| **Switch** | Data Link (L2) | Intelligent hub, **MAC address table** for forwarding, **increases collision domains** |
| **Router** | Network (L3) | Forwards packets between networks, **path selection and routing** |
| **Firewall** | Network+ | **Stops unauthorized access**, filters traffic based on rules |

### 1.4 Key Exam Facts about Switches
- Switch resolves forwarding using **MAC address table** (bridging table)
- Switch matches **unicast destination address** to MAC address table
- Switches **increase collision domains** (each port = separate collision domain)
- Switches do NOT filter based on IP (routers do)
- Switches forward broadcasts (routers do not by default)

### 1.5 Hubs vs Switches
| Feature | Hub | Switch |
|---------|-----|--------|
| Layer | Physical (L1) | Data Link (L2) |
| Frame filtering | **Cannot filter** | Filters by MAC address |
| Collision domain | Single domain | Each port = separate domain |
| Broadcast | Forwards to all | Forwards to all |
| Processing speed | Faster (no processing) | Slower (processes each frame) |

### 1.6 Cross-over vs Straight-through UTP
- **Straight-through**: connects different device types (switch ↔ PC, router ↔ switch)
- **Cross-over**: connects same device types (switch ↔ switch, **pc ↔ pc**, router ↔ PC)
- Cross-over is **NOT** used for: switch to PC (that's straight-through)

---

## LO2: OSI & TCP/IP Models (6 items)

### 2.1 OSI Model (7 Layers) — Bottom to Top
```
7. Application     ┐
6. Presentation     │ Host layers
5. Session         ┘
4. Transport       ─────
3. Network         ┐
2. Data Link        │ Media layers
1. Physical        ┘
```

### 2.2 Layer Functions (Exam Priority!)
| Layer | PDU | Function | Device |
|-------|-----|----------|--------|
| **7. Application** | Data | Process-to-process interaction, user services (HTTP, FTP, SMTP, DNS) | — |
| **6. Presentation** | Data | Data format translation, encryption, compression | — |
| **5. Session** | Data | Session establishment, management, termination | — |
| **4. Transport** | **Segment** | End-to-end delivery, reliability (TCP), flow control | — |
| **3. Network** | **Packet** | **Addressing, path selection, routing** | **Router** |
| **2. Data Link** | **Frame** | Framing, MAC addressing, error detection | **Switch, Bridge** |
| **1. Physical** | **Bit** | Electrical/mechanical transmission, cables | **Hub, Repeater** |

### 2.3 PDU Order (Bottom → Top)
```
Bit → Frame → Packet → Segment → Data
```
- As data moves **bottom to top**: receives bits, reassembles into frames, extracts packets, segments, finally data

### 2.4 TCP/IP Model (4 Layers)
```
4. Application     ─ (combines OSI 5-6-7)
3. Transport       ─ (same as OSI)
2. Internet        ─ (same as OSI Network layer — routing, addressing)  
1. Network Access  ─ (combines OSI 1-2)
```

**TCP/IP Internet Layer** = responsible for **addressing, path selection, and routing**

### 2.5 Transport Layer: TCP vs UDP
| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable (ACKs, retransmission) | Unreliable (best effort) |
| Ordering | Preserves order | No ordering |
| Flow control | Yes | No |
| Speed | Slower | Faster |
| Use cases | Web (HTTP), Email (SMTP), File (FTP) | Streaming, DNS, VoIP, DHCP |

### 2.6 Data Link Sublayers
Two sublayers of Layer 2:
1. **Logical Link Control (LLC)**: **identifies Network layer protocols** and encapsulates them
2. **Media Access Control (MAC)**: handles addressing, access to physical medium

### 2.7 Data Link Layer Technologies
- **PPP** (Point-to-Point Protocol) ✓
- **Frame Relay** ✓
- **VLAN** (Virtual LAN) ✓
- **OSPF** ✗ — OSPF is a **Network layer** routing protocol, NOT a data link technology

### 2.8 Application Layer Protocols
| Protocol | Port | Function |
|----------|------|----------|
| HTTP | 80 | Web browsing |
| HTTPS | 443 | Secure web browsing |
| FTP | 21 | File transfer |
| SSH | 22 | Secure remote shell |
| Telnet | 23 | Unsecured remote terminal |
| SMTP | 25 | Email sending |
| DNS | 53 | Domain name resolution |
| DHCP | 67/68 | Dynamic IP address assignment |
| POP3 | 110 | Email retrieval |
| IMAP | 143 | Email retrieval (with server folders) |

---

## LO3: Network Services & Design (Part of remaining items)

### 3.1 IPv4 Addressing
**Structure**: 32-bit, dotted decimal notation (e.g., 192.168.1.1)

**IPv4 Address Classes**:
| Class | First Octet | Default Mask | Network/Host Bits |
|-------|-------------|-------------|------------------|
| A | 1-126 | /8 (255.0.0.0) | N.H.H.H |
| B | 128-191 | /16 (255.255.0.0) | N.N.H.H |
| C | 192-223 | /24 (255.255.255.0) | N.N.N.H |
| D | 224-239 | Multicast | — |
| E | 240-255 | Reserved | — |

**Special Addresses**:
- Network address: all host bits = 0 (e.g., 172.17.128.0/21)
- Broadcast address: all host bits = 1 (e.g., 172.17.135.255/21)
- Valid host range: between network and broadcast addresses

**Subnetting Example (from AAU 2015 Q4)**:
Network: `172.17.128.0/21`
- /21 → 255.255.248.0
- Block size = 256 - 248 = 8 (in the third octet)
- Network ranges: 172.17.128.0 → 172.17.135.255
- Valid hosts: 172.17.128.1 → 172.17.135.254
- **Invalid hosts**: 172.17.128.0 (network), 172.17.135.255 (broadcast)
- But also check: `172.17.135.0/21` — is it valid? Yes, it's within range (128-135).
- `172.17.128.255/21` — is it valid? Yes (it's not a broadcast for this subnet).

### 3.2 ACLs (Access Control Lists)
- Sequential list of permit/deny statements
- **Implicit deny** at the end of every ACL
- Compared with each line in **sequential order** until match
- Once a match is found, the packet is **permitted or denied immediately**
- Benefits: **classifies and organizes network traffic**, provides security, traffic filtering

### 3.3 Ethernet & Collisions
- **Half-duplex Ethernet**: only one device can transmit at a time
- **Collision**: two hosts transmit at the same time in half-duplex
- After collision: **jam signal** → hosts wait a random backoff time → retransmit
- Switches **increase collision domains** (each port isolated)
- Hubs create a single collision domain

### 3.4 Firewalls & Secure Channels
- **Firewall**: stops **unauthorized access by hackers** (NOT virus scanning, NOT fire spreading)
- **SSH (Secure Shell)**: secure remote connection, port 22
- **SSL/TLS**: secure web communication, used by HTTPS
- Both SSH and SSL establish **secure channel** between local and remote

### 3.5 Network Security Basics
- **Confidentiality**: preventing unauthorized disclosure
- **Integrity**: preventing unauthorized modification
- **Availability**: ensuring access when needed
- **AAA**: Authentication, Authorization, Accounting

---

## Exam-Style Q&A (From 18 Actual Model Exam Questions)

**Q1:** Which layer of TCP/IP is responsible for addressing, path selection, and routing?
- a. Application layer
- b. **Internet layer** ✓
- c. Transport layer
- d. Network Access layer

**Q2:** Correct order of PDUs as data moves bottom to top in OSI model?
- a. Segment, Packet, Frame, Bit
- b. Segment, Frame, Packet, Bit
- c. **Bit, Frame, Packet, Segment** ✓
- d. Bit, Packet, Frame, Segment

**Q3:** A firewall is used to?
- a. Fire spreading via network cables
- b. Avoid spreading of fire
- c. **Stop unauthorized access by hackers** ✓
- d. Scanning for viruses

**Q4:** A TCP/IP port number used by SSH is?
- a. 20
- b. 23
- c. **22** ✓
- d. 21

**Q5:** How does a switch resolve forwarding for a unicast MAC address?
- a. **Matches destination MAC to MAC address table** ✓
- b. Matches destination IP to MAC
- c. Matches incoming interface to source MAC
- d. Matches source address to MAC table

**Q6:** Which data link sublayer identifies Network layer protocols?
- a. Frame relay
- b. MAC
- c. **LLC (Logical Link Control)** ✓
- d. PPP

**Q7:** Which is NOT a data link layer technology?
- a. **OSPF** ✓ (it's a routing protocol at Network layer)
- b. PPP
- c. Frame-relay
- d. VLAN

**Q8:** False statement about ACLs?
- a. Implicit deny at end ✓ (true statement)
- b. Comparison continues until all lines analyzed ✓ (true statement)
- c. Compared with each line sequentially ✓ (true statement)
- d. Once match found, packet is processed ✓ (true)
- **Trick**: The question asked for FALSE — all above are TRUE. The false one from the exam was: "packet is stopped" — actually once matched, it's permitted or denied.

**Q9:** Which is true regarding switches and hubs?
- a. Switches do not forward broadcasts (FALSE — they do)
- b. **Switches increase collision domains** ✓
- c. Switches take less time than hubs (FALSE — hubs are faster/no processing)
- d. Hubs can filter frames (FALSE — hubs cannot filter)

**Q10:** After a collision on half-duplex Ethernet, what happens?
- a. Jam signal clears the collision
- b. Electrical pulse clears it
- c. **Hosts retransmit after a time delay** ✓
- d. Router signals the collision cleared

**Q11:** Cross-over UTP cable is NOT used for?
- a. Switch to switch
- b. PC to PC
- c. Router to PC
- d. **Switch to PC** ✓ (that's straight-through)

**Q12:** What describes a secure channel between local and remote computer?
- a. SSL
- b. **SSH** ✓ (exam answer — SSH is the set of standards and protocol)
- c. AAA
- d. SNMP

**Q13:** Application layer functionalities?
- a. **Process to process interaction** ✓
- b. Mechanical, electrical, physical connectivity (Physical layer)
- c. Encapsulation of frames (Data Link layer)
- d. Encapsulation of packets (Network layer)

**Q14:** Benefits of ACLs for software security?
- a. Monitor bytes and packets
- b. Provide high network availability
- c. Virus detection
- d. **Classify and organize network traffic** ✓

**Q15:** Which is a unique IPv4 address?
- From the options, look for an address that is NOT the network address or broadcast address within its subnet
- 172.17.17.17/26 is unique (not network/broadcast)

**Q16:** HTTP request message always contains?
- a. A status line, a header, and a body
- b. A header only
- c. A header and a body
- d. **A request line and a header** ✓

---

## Quick Reference — Blueprint Table

| LO | Topic | Items | Cognitive |
|----|-------|-------|-----------|
| 1 | Network fundamentals concepts | 2 | 1 Rem, 1 Und |
| 2 | Analyze networking layers | 6 | 3 Und, 3 App |
| 3 | Design network services | 4 | 2 App, 2 Ana |
| **Total** | | **8** | |
