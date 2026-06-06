# Day 10 — Networking Trace Exercises & Problem-Solving (Exam-Style)

## Set 1: OSI Model Trace

### Problem 1 — Layer Identification
Match the function to the OSI layer:
1. Addressing, path selection, routing → _________
2. Framing, MAC addressing → _________
3. Application services (HTTP, FTP) → _________
4. Reliable end-to-end delivery → _________
5. Electrical signal transmission → _________

**Solution:**
1. Network (L3) — packet forwarding
2. Data Link (L2) — frame creation
3. Application (L7) — user services
4. Transport (L4) — TCP/UDP segments
5. Physical (L1) — bits

---

### Problem 2 — PDU Order
Place these PDUs in the correct order as data travels from the **top (application) to the bottom (physical)**:
- Frame
- Packet
- Bit
- Segment
- Data

**Solution (top→bottom):** Data → Segment → Packet → Frame → Bit
- Data at Application/Presentation/Session
- Segment at Transport
- Packet at Network
- Frame at Data Link
- Bit at Physical

---

### Problem 3 — Bottom-to-Top PDU Order
Same PDUs moving **bottom to top** (from physical to application):

**Solution:** Bit → Frame → Packet → Segment → Data

---

### Problem 4 — TCP/IP Layer Mapping
Map OSI layers to TCP/IP model:
a) Which TCP/IP layer combines OSI 5, 6, 7?
b) Which TCP/IP layer handles routing?
c) Which TCP/IP layer combines OSI 1, 2?

**Solution:**
a) Application layer
b) Internet layer (same as OSI Network layer)
c) Network Access layer

---

## Set 2: Device & Technology Trace

### Problem 5 — Device to Layer
Match device to OSI layer:
1. Hub → _________
2. Switch → _________
3. Router → _________
4. Repeater → _________
5. Bridge → _________

**Solution:**
1. Physical (L1)
2. Data Link (L2)
3. Network (L3)
4. Physical (L1)
5. Data Link (L2)

---

### Problem 6 — Switch Forwarding Trace
A switch receives a frame with destination MAC AA:BB:CC:DD:EE:FF. The switch's MAC address table has:
```
MAC Address        Port
AA:BB:CC:DD:EE:01  Port 1
AA:BB:CC:DD:EE:02  Port 2
AA:BB:CC:DD:EE:03  Port 3
```
What does the switch do?

**Solution:** The destination MAC (AA:BB:CC:DD:EE:FF) is **not in the table** → the switch **floods** the frame out all ports (except the incoming port). This is the learning/forwarding process.

---

### Problem 7 — Hub vs Switch
In a network with 10 devices:
a) Using a **hub**: how many collision domains?
b) Using a **switch**: how many collision domains?

**Solution:**
a) **1 collision domain** (all devices share the same medium on a hub)
b) **10 collision domains** (each switch port is a separate collision domain)

---

### Problem 8 — Cable Selection
Which cable type (straight-through or cross-over) for each connection?
a) Switch to PC → _________
b) Switch to switch → _________
c) PC to PC → _________
d) Router to switch → _________
e) Router to PC → _________

**Solution:**
a) Straight-through
b) Cross-over
c) Cross-over
d) Straight-through
e) Cross-over

---

## Set 3: Subnetting Trace

### Problem 9 — Subnet Analysis
Network: `192.168.50.0/26`

a) What is the subnet mask?
b) How many usable hosts?
c) What is the network address?
d) What is the broadcast address?
e) What is the valid host range?

**Solution:**
a) /26 = 255.255.255.192
b) 2^(32-26) - 2 = 2^6 - 2 = 64 - 2 = **62 usable hosts**
c) 192.168.50.0 (network address)
d) 192.168.50.63 (broadcast — 0 + 64 - 1 = 63)
e) 192.168.50.1 → 192.168.50.62

---

### Problem 10 — Valid Host Check (AAU 2015 Style)
Which is NOT a valid host in network `172.17.128.0/21`?
a) 172.17.128.1/21
b) 172.17.135.255/21
c) 172.17.128.255/21
d) 172.17.135.0/21

**Solution:**
- /21 → mask = 255.255.248.0
- Block size = 256 - 248 = 8 (in third octet)
- Network ranges: 172.17.**128**.0 → 172.17.**135**.255
- Network address: 172.17.128.0 (all host bits 0)
- Broadcast address: 172.17.135.255 (all host bits 1)
- Valid range: 172.17.128.1 → 172.17.135.254

a) 172.17.128.1/21 — **VALID** (within range)
b) 172.17.135.255/21 — **INVALID** (broadcast address of this subnet)
c) 172.17.128.255/21 — **VALID** (not a broadcast)
d) 172.17.135.0/21 — **VALID** (within range, not network/broadcast)

**Answer: b) 172.17.135.255/21 is NOT a valid host**

---

### Problem 11 — Class Identification
Classify each IP address:
a) 10.0.0.1 → Class ___
b) 172.16.0.1 → Class ___
c) 192.168.1.1 → Class ___
d) 126.0.0.1 → Class ___
e) 200.1.1.1 → Class ___

**Solution:**
a) Class A (10.x.x.x = 1-126)
b) Class B (172.16.x.x = 128-191)
c) Class C (192.168.x.x = 192-223)
d) Class A (126 = 1-126 range)
e) Class C (200 = 192-223 range)

---

## Set 4: Protocol & Port Trace

### Problem 12 — Port Matching
Match protocol to port:
1. HTTP → a. 22
2. HTTPS → b. 53
3. SSH → c. 80
4. FTP → d. 443
5. DNS → e. 21
6. SMTP → f. 25

**Solution:** 1-c, 2-d, 3-a, 4-e, 5-b, 6-f

---

### Problem 13 — TCP vs UDP
Classify each protocol as TCP or UDP:
a) HTTP → ___
b) DNS → ___
c) FTP → ___
d) DHCP → ___
e) SMTP → ___
f) VoIP → ___

**Solution:**
a) TCP (reliable, web browsing)
b) **UDP** (quick queries, one packet)
c) TCP (reliable file transfer)
d) **UDP** (broadcast-based discovery)
e) TCP (reliable mail delivery)
f) **UDP** (real-time, can tolerate loss)

---

### Problem 14 — LLC Sublayer
Which data link sublayer is responsible for identifying the Network layer protocol (e.g., IPv4 or IPv6) and encapsulating the packet into a frame?

**Solution:** **LLC (Logical Link Control)** — the upper sublayer of Data Link layer

---

## Set 5: Collision & Ethernet Trace

### Problem 15 — Collision Trace
On a half-duplex Ethernet LAN, Host A and Host B transmit at the same time.

1. What happens?
2. What signal is sent to indicate the collision?
3. What do the hosts do next?

**Solution:**
1. A **collision** occurs
2. A **jam signal** is sent to notify all devices
3. Each host waits a **random backoff time** (exponential backoff), then attempts retransmission

---

### Problem 16 — ACL Trace
An ACL has these rules:
```
1. permit 192.168.1.0/24
2. deny 10.0.0.0/8
3. permit any
```
A packet from 10.0.0.5 arrives. What happens?

**Solution:**
- Rule 1: 10.0.0.5 is not in 192.168.1.0/24 → no match
- Rule 2: 10.0.0.5 matches 10.0.0.0/8 → **DENIED** (packet dropped)
- Rule 3 is never reached

---

### Problem 17 — Implicit Deny
An ACL has only one rule:
```
permit 192.168.1.0/24
```
A packet from 172.16.0.1 arrives. What happens?

**Solution:** The packet does not match the permit rule. The **implicit deny** at the end of the ACL blocks it. The packet is **dropped**.

---

## Set 6: Security & Firewall

### Problem 18 — Firewall Purpose
A company installs a firewall between its internal network and the internet. Which of the following is the primary purpose?
a) Preventing fire from spreading through cables
b) Scanning emails for viruses
c) **Stopping unauthorized access by hackers**
d) Monitoring employee internet usage

**Solution:** c) Firewalls control access based on security rules — primarily to stop unauthorized access

---

### Problem 19 — Secure Protocol
A system administrator needs to securely connect to a remote server's command line over the internet. Which protocol should they use?
a) Telnet (port 23)
b) **SSH (port 22)**
c) FTP (port 21)
d) HTTP (port 80)

**Solution:** b) SSH provides encrypted remote shell access. Telnet is unencrypted.

---

### Problem 20 — Identify the Device
A network device receives a frame and forwards it based on the destination MAC address. It has 24 ports, each in a separate collision domain. What is this device?

**Solution:** **Switch** — operates at Layer 2, uses MAC address table, creates separate collision domains per port

---

## Common Exam Traps — Networking

| Trap | Explanation |
|------|-------------|
| **TCP/IP routing layer** | Internet layer handles **addressing, path selection, routing** (not Network Access) |
| **PDU order bottom→top** | **Bit → Frame → Packet → Segment** (NOT Segment→Packet→Frame→Bit) |
| **Switch forwarding** | Matches **destination MAC** to MAC address table (not source, not IP) |
| **LLC sublayer** | LLC identifies **Network layer** protocols (not MAC) |
| **OSPF is NOT data link** | OSPF = routing protocol at **Network layer**, not Data Link |
| **Hub cannot filter** | Hubs operate at **Physical layer**, cannot filter frames (switches can) |
| **Collision response** | After collision: **jam signal → backoff → retransmit** |
| **Cross-over NOT for** | Switch ↔ PC uses **straight-through**, not cross-over |
| **Implicit ACL deny** | There's an **implicit deny** at the end of every ACL |
| **Firewall purpose** | Stop **unauthorized access** (not viruses, not fire) |
| **SSH vs SSL** | SSH = secure **shell** (remote access); SSL = secure **sockets** (web) |
| **Valid host check** | Network address (all host bits 0) and broadcast (all 1s) are NOT valid hosts |
| **Application layer** | Process-to-process interaction (not physical connectivity) |
