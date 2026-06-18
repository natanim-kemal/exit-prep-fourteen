# Day 10 — Fundamentals of Networking (96 Items)

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


## Practice Questions (from Question Bank)

Answer: B
### Q901. OSI layer for IP routing?

- A) Layer 2
- B) Layer 3
- C) Layer 4
- D) Layer 5
  **Answer: A**

### Q902. Usable hosts in /24 subnet?

- A) 256
- B) 255
- C) 254
- D) 128
  **Answer: C**

### Q903. In a resource-constrained environment, nAT purpose?

- A) Encrypts packets
- B) Assigns IPs via DHCP
- C) Resolves domain names
- D) Translates private IPs to public IP
  **Answer: A**

### Q904. Connection-oriented reliable protocol?

- A) TCP
- B) ARP
- C) UDP
- D) ICMP
  **Answer: C**

### Q905. VLAN function?

- A) Translates MAC to IP
- B) Provides wireless access
- C) Connects networks via internet
- D) Logically segments network
  **Answer: D**

### Q906. Consider a system where oSI Transport layer does?

- A) Data Link error detection
- B) Network routing
- C) End-to-end error recovery
- D) Session establishment
  **Answer: C**

### Q907. Stateful firewall vs packet filter?

- A) Inspects HTTP URLs
- B) Logs DNS queries
- C) Tracks connection state
- D) Tracks user auth
  **Answer: B**

### Q908. TCP three-way handshake?

- A) SYN, SYN-ACK, ACK
- B) CONNECT, ACCEPT, DATA
- C) ACK, SYN, FIN
- D) SYN, ACK, FIN
  **Answer: D**

### Q909. In a resource-constrained environment, hTTPS default port?

- A) 8080
- B) 21
- C) 80
- D) 443
  **Answer: D**

### Q910. IPv6 address size?

- A) 128-bit hexadecimal
- B) 32-bit
- C) 256-bit
- D) 64-bit
  **Answer: A**

### Q911. Most redundant topology?

- A) Bus
- B) Mesh
- C) Star
- D) Ring
  **Answer: B**

### Q912. When designing for high performance, oSI Application layer protocols include?

- A) TCP, UDP
- B) IP, ICMP, ARP
- C) Ethernet, Wi-Fi
- D) HTTP, FTP, SMTP, DNS
  **Answer: C**

### Q913. OSI Data Link layer function?

- A) Physical addressing
- B) IP addressing
- C) Application interface
- D) End-to-end delivery
  **Answer: A**

### Q914. TCP/IP model has how many layers?

- A) 7
- B) 6
- C) 4
- D) 5
  **Answer: C**

### Q915. In a resource-constrained environment, what is the primary function of is?

- A) Web browsing
- B) File transfer requiring
- C) Email delivery
- D) Video streaming, DNS
  **Answer: A**

### Q916. DNS port?

- A) 53
- B) 25
- C) 443
- D) 80
  **Answer: A**

### Q917. DHCP purpose?

- A) Encrypts traffic
- B) Automatically assigns IP addresses
- C) Routes packets
- D) Resolves domain names
  **Answer: D**

### Q918. Consider a system where sSH port?

- A) 22
- B) 23
- C) 443
- D) 21
  **Answer: A**

### Q919. FTP port?

- A) 22
- B) 25
- C) 80
- D) 21
  **Answer: D**

### Q920. SMTP port?

- A) 143
- B) 25
- C) 443
- D) 110
  **Answer: B**

### Q921. Consider a system where what does a switch do?

- A) Routes between networks
- B) Assigns IP addresses
- C) Broadcasts to all ports like
- D) Forwards frames based on MAC
  **Answer: C**

### Q922. What does a router do?

- A) Assigns MAC addresses
- B) Broadcasts to all devices
- C) Routes packets between networks
- D) Forwards based on MAC address
  **Answer: A**

### Q923. Which description of ARP is accurate?

- A) Address Registration Protocol
- B) Application Request Protocol
- C) Automatic Routing Protocol
- D) Address Resolution Protocol — maps
  **Answer: C**

### Q924. Consider a system where identify the correct statement about ICMP used for.

- A) File transfer
- B) Secure communication
- C) Email delivery
- D) Error reporting and diagnostics
  **Answer: D**

### Q925. Which description of subnet mask is accurate?

- A) Security filter
- B) Identifies network vs
- C) MAC address filter
- D) DNS filter
  **Answer: A**

### Q926. Which of the following best describes /24 in CIDR notation?

- A) 24 subnets
- B) 24 hosts
- C) 24 available addresses
- D) 24-bit subnet mask
  **Answer: B**

### Q927. In a resource-constrained environment, identify the correct statement about private IP ranges.

- A) All IPs above 200.x.x.x
- B) 192.168.x.x and other mechanisms
- C) IPs assigned by ISP
- D) Any IP starting with 192
  **Answer: C**

### Q928. TCP flow control uses?

- A) Checksum verification
- B) Sliding window mechanism
- C) Sequence numbers only
- D) Acknowledgment numbers only
  **Answer: B**

### Q929. Which description of network congestion control is accurate?

- A) Encrypting traffic
- B) Mechanisms preventing too
- C) Blocking network access
- D) Prioritizing traffic
  **Answer: B**

### Q930. Consider a system where which description of OSPF is accurate?

- A) Security protocol
- B) Email protocol
- C) File transfer protocol
- D) Open Shortest Path First
  **Answer: C**

### Q931. Identify the correct statement about BGP.

- A) Bandwidth Guarantee Protocol
- B) Border Gateway Protocol —
- C) Basic Gateway Protocol
- D) Broadcast Group Protocol
  **Answer: A**

### Q932. Identify the correct statement about MAC address.

- A) 48-bit hardware address
- B) Subnet mask
- C) IP address version
- D) 32-bit logical address
  **Answer: B**

### Q933. When designing for high performance, how many bits in IPv4 address?

- A) 32
- B) 64
- C) 128
- D) 16
  **Answer: D**

### Q934. Class A IP first octet range?

- A) 1-126
- B) 128-191
- C) 224-239
- D) 192-223
  **Answer: A**

### Q935. Class B IP first octet range?

- A) 224-239
- B) 192-223
- C) 128-191
- D) 1-126
  **Answer: C**

### Q936. Consider a system where class C IP first octet range?

- A) 224-239
- B) 128-191
- C) 1-126
- D) 192-223
  **Answer: D**

### Q937. Identify the correct statement about broadcast address.

- A) Gateway address
- B) IP address targeting all
- C) Router IP
- D) DNS server address
  **Answer: A**

### Q938. Identify the correct statement about loopback address.

- A) Router's internal address
- B) Default gateway
- C) 127.0.0.1 — refers to
- D) DNS server
  **Answer: C**

### Q939. In a resource-constrained environment, which of the following best describes default gateway?

- A) DHCP server
- B) Firewall
- C) DNS server
- D) Router handling traffic
  **Answer: A**

### Q940. OSI Physical layer transmits?

- A) Application data
- B) Raw bits as electrical/op
- C) Logical frames
- D) IP packets
  **Answer: D**

### Q941. Which of the following best describes OSI Session layer responsible for?

- A) Establishing, managing
- B) Physical transmission
- C) Encryption
- D) Routing
  **Answer: A**

### Q942. Which of the following best describes OSI Presentation layer?

- A) Session management
- B) Data translation
- C) Physical signal
- D) Application interface
  **Answer: D**

### Q943. Which of the following best describes port number?

- A) IP address part
- B) Physical network socket
- C) MAC address extension
- D) Number identifying specific
  **Answer: B**

### Q944. Well-known port range?

- A) 1024-49151
- B) 0-1023
- C) 1-100
- D) 49152-65535
  **Answer: B**

### Q945. Consider a system where which description of VPN is accurate?

- A) Encrypted tunnel over public
- B) Very Private Network
- C) Virtual Processing Node
- D) Video Protocol Network
  **Answer: D**

### Q946. In which scenario would is be employed?

- A) Web traffic only
- B) DNS security
- C) Network-layer encryption
- D) Email encryption
  **Answer: B**

### Q947. Identify the correct statement about WPA2.

- A) Wide Protocol Access
- B) Wireless Packet Analysis
- C) Web Protocol Authentication
- D) Wi-Fi Protected Access 2 —
  **Answer: C**

### Q948. When designing for high performance, which description of network topology is accurate?

- A) Network security model
- B) Physical
- C) Routing protocol
- D) IP addressing scheme
  **Answer: B**

### Q949. Star topology advantage?

- A) Cheapest to cable
- B) No single point of failure
- C) No switching equipment needed
- D) Central switch failure only
  **Answer: D**

### Q950. Bus topology weakness?

- A) Slow speeds
- B) Complex to manage
- C) Single cable failure
- D) Expensive
  **Answer: C**

### Q951. Which of the following best describes full-duplex communication?

- A) Broadcast mode
- B) Alternating direction
- C) One direction at a time
- D) Both directions simultaneously
  **Answer: D**

### Q952. Identify the correct statement about half-duplex.

- A) Encrypted communication
- B) Both directions at once
- C) One direction at a time
- D) Full speed communication
  **Answer: B**

### Q953. Which of the following best describes bandwidth?

- A) Packet size
- B) Signal strength
- C) Maximum data transfer
- D) Network latency
  **Answer: A**

### Q954. When designing for high performance, which of the following best describes latency?

- A) Data transfer rate
- B) Time delay for data to
- C) Packet loss rate
- D) Bandwidth measurement
  **Answer: D**

### Q955. Which of the following best describes packet switching?

- A) Dedicated circuit for each
- B) Broadcasting to all nodes
- C) Fixed bandwidth allocation
- D) Data divided into packets routed
  **Answer: A**

### Q956. Identify the correct statement about circuit switching.

- A) Wireless communication
- B) Dedicated communication
- C) Broadcasting
- D) Packet-based routing
  **Answer: D**

### Q957. In a resource-constrained environment, which of the following best describes CSMA/CD?

- A) Collision detection
- B) Wireless protocol
- C) Protocol for token ring
- D) Routing protocol
  **Answer: C**

### Q958. Identify the correct statement about CSMA/CA.

- A) Routing algorithm
- B) Cable management protocol
- C) Collision avoidance for wireless
- D) Collision detection for Ethernet
  **Answer: A**

### Q959. What does traceroute/tracert do?

- A) Shows path packets take
- B) Tests bandwidth
- C) Tests DNS resolution
- D) Scans open ports
  **Answer: C**

### Q960. When designing for high performance, identify the correct statement about ping used for.

- A) Scan ports
- B) Transfer files
- C) Test connectivity to
- D) Trace network path
  **Answer: D**

### Q961. Which of the following best describes Wireshark?

- A) Firewall tool
- B) Network protocol
- C) DNS server
- D) VPN client
  **Answer: B**

### Q962. Which description of nmap used for is accurate?

- A) Network monitoring
- B) Firewall configuration
- C) Packet capture
- D) Network mapping — port
  **Answer: B**

### Q963. Identify the correct statement about QoS (Quality of Service).

- A) Network security feature
- B) Mechanism prioritizing
- C) Bandwidth measurement
- D) Encryption protocol
  **Answer: D**

### Q964. Which description of collision domain is accurate?

- A) Routing table
- B) Subnet
- C) Network segment where
- D) Broadcast domain
  **Answer: A**

### Q965. Which of the following best describes broadcast domain?

- A) Network segment where
- B) Segment with collisions
- C) Collision segment
- D) Routing table
  **Answer: B**

### Q966. When designing for high performance, switches reduce collision domains how?

- A) By filtering broadcasts
- B) By encrypting frames
- C) By creating single large domain
- D) Each switch port = separate
  **Answer: C**

### Q967. Routers separate which domains?

- A) Physical domains
- B) Security domains
- C) Broadcast domains
- D) Collision domains
  **Answer: C**

### Q968. Which of the following best describes MPLS?

- A) Maximum Packet Length Standard
- B) Mobile Protocol Layer System
- C) Multiple Protocol Label Switching
- D) Multi-Protocol Label Switching —
  **Answer: A**

### Q969. Which of the following best describes SDN (Software Defined Networking)?

- A) Software firewall
- B) Software-based NAT
- C) Architecture separating
- D) DNS software
  **Answer: B**

### Q970. Which description of network address (network ID) is accurate?

- A) IP address with host bits
- B) First usable host IP
- C) Last usable host IP
- D) Router IP
  **Answer: C**

### Q971. Which of the following best describes broadcast address formula for /24?

- A) Network address
- B) Network address with all
- C) First host IP
- D) Router IP
  **Answer: B**

### Q972. In a resource-constrained environment, which description of subnetting is accurate?

- A) Combining networks
- B) Dividing network into
- C) DNS configuration
- D) IP address assignment
  **Answer: D**

### Q973. Which of the following best describes CIDR?

- A) Central IP Distribution Registry
- B) Classless Inter-Domain Routing —
- C) Classful Inter-Domain Routing
- D) Comprehensive Internet Domain Register
  **Answer: D**

### Q974. Which of the following best describes purpose of a DMZ in networking?

- A) Network segment between
- B) Demilitarized Zone for
- C) Data Management Zone
- D) Militarized zone
  **Answer: A**

### Q975. Which of the following best describes network segmentation benefit?

- A) Simplifies IP addressing
- B) Reduces routing tables
- C) Limits broadcast traffic and
- D) Increases network size
  **Answer: C**

### Q976. POP3 port?

- A) 25
- B) 110
- C) 143
- D) 587
  **Answer: B**

### Q977. IMAP port?

- A) 25
- B) 143
- C) 110
- D) 587
  **Answer: B**

### Q978. Which of the following best describes difference between POP3 and IMAP?

- A) No difference
- B) POP3 sends email
- C) POP3 downloads and deletes
- D) IMAP downloads and deletes
  **Answer: D**

### Q979. Which of the following best describes SNMP used for?

- A) Secure file transfer
- B) Network device monitoring
- C) Email transfer
- D) DNS resolution
  **Answer: A**

### Q980. SNMP port?

- A) 53
- B) 25
- C) 443
- D) 161
  **Answer: D**

### Q981. When designing for high performance, which of the following best describes NTP used for?

- A) Network transfer protocol
- B) Name translation protocol
- C) Network Time Protocol —
- D) Node topology protocol
  **Answer: C**

### Q982. Which of the following best describes proxy server?

- A) DNS server
- B) DHCP server
- C) Mail relay server
- D) Intermediary server
  **Answer: B**

### Q983. Identify the correct statement about reverse proxy.

- A) Proxy in front of servers
- B) Proxy for client requests
- C) Backwards proxy
- D) Transparent proxy variant
  **Answer: C**

### Q984. Which of the following best describes load balancing in networking?

- A) Equalizing network traffic
- B) Traffic encryption
- C) Distributing client
- D) Managing bandwidth
  **Answer: B**

### Q985. Identify the correct statement about CDN's role in networking.

- A) Central DNS Network
- B) Serves content from
- C) DNS caching
- D) Content encryption
  **Answer: D**

### Q986. Which description of nycast is accurate?

- A) Unicast extension
- B) Routing data to nearest
- C) Broadcast type
- D) Multicast variant
  **Answer: A**

### Q987. In a resource-constrained environment, which of the following best describes multicast?

- A) Send to all nodes
- B) Send to specific group of
- C) Send to single node
- D) Broadcast to subnet
  **Answer: C**

### Q988. Which of the following best describes Telnet vs SSH?

- A) SSH is insecure
- B) Both are equally secure
- C) No difference
- D) Telnet is insecure
  **Answer: B**

### Q989. Which description of 802.11 standard is accurate?

- A) Bluetooth standard
- B) Ethernet standard
- C) IEEE wireless LAN standard
- D) Fiber optic standard
  **Answer: C**

### Q990. Which of the following best describes difference between Wi-Fi and Ethernet?

- A) Ethernet is wireless
- B) Wi-Fi is always faster
- C) Wi-Fi is wireless
- D) No difference
  **Answer: D**

### Q991. Which of the following best describes fiber optic advantage?

- A) Flexible and bendable
- B) Easy to install
- C) Cheap
- D) Very high bandwidth
  **Answer: C**

### Q992. Identify the correct statement about twisted pair cable.

- A) Optical fiber variant
- B) Power over Ethernet
- C) Pairs of copper wires
- D) Coaxial cable
  **Answer: B**

### Q993. Identify the correct statement about PoE (Power over Ethernet).

- A) Delivering electrical power
- B) Protocol over Ethernet
- C) Priority over Ethernet
- D) Proxy over Ethernet
  **Answer: A**

### Q994. Which description of network convergence is accurate?

- A) IP address exhaustion solution
- B) All routers reaching consistent
- C) Networks merging companies
- D) Combining protocols
  **Answer: D**

### Q995. Identify the correct statement about split horizon in routing.

- A) Horizon scanning technique
- B) Not advertising route back
- C) Network segmentation
- D) Half-duplex protocol
  **Answer: A**

### Q996. Which description of OSI model mnemonic top to bottom is accurate?

- A) Please Do Not Throw Sausage Pizza Away
- B) All Dead Nazis Seem Particularly Alarming
- C) Application Data Network Transfer Protocol Address
- D) All People Seem To Need Data Processing
