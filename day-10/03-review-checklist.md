# Day 10 — Fundamentals of Networking Review Checklist

## Mastery Checklist

### LO1: Network Fundamentals (2 items)
- [ ] Network types: LAN, WAN, MAN, PAN
- [ ] Topologies: Bus, Star, Ring, Mesh, Tree — pros/cons
- [ ] Hub (L1): broadcasts to all, cannot filter, single collision domain
- [ ] Switch (L2): MAC address table, increases collision domains, filters by MAC
- [ ] Router (L3): path selection, routing, connects different networks
- [ ] Firewall: stops unauthorized access (not virus scanning)
- [ ] **Cross-over** UTP: switch↔switch, PC↔PC, router↔PC (same type)
- [ ] **Straight-through** UTP: switch↔PC, router↔switch (different types)
- [ ] Repeater (L1): regenerates signal
- [ ] Bridge (L2): connects segments, filters by MAC

### LO2: OSI & TCP/IP Models (6 items)
- [ ] **OSI 7 layers** (bottom→top): Physical, Data Link, Network, Transport, Session, Presentation, Application
- [ ] PDU order (bottom→top): **Bit → Frame → Packet → Segment → Data**
- [ ] **Physical (L1)**: electrical/mechanical, bits, cables — devices: Hub, Repeater
- [ ] **Data Link (L2)**: framing, MAC, LLC, error detection — devices: Switch, Bridge
- [ ] **LLC sublayer**: identifies Network layer protocols
- [ ] **Network (L3)**: **addressing, routing, path selection** — devices: Router
- [ ] **Transport (L4)**: end-to-end, segmentation, TCP/UDP
- [ ] **Application (L7)**: process-to-process interaction, user services
- [ ] **TCP/IP 4 layers**: Application, Transport, **Internet**, Network Access
- [ ] TCP: connection-oriented, reliable, ordered, slower
- [ ] UDP: connectionless, unreliable, unordered, faster (DNS, DHCP, VoIP)
- [ ] Data link technologies: PPP, Frame Relay, VLAN ✓ — **OSPF is NOT** (it's routing)
- [ ] ACLs: sequential, implicit deny, classifies/organizes traffic

### LO3: Network Services & Design
- [ ] IPv4 classes: A(1-126), B(128-191), C(192-223)
- [ ] Subnetting: network address (all host bits 0), broadcast (all 1s), valid hosts in between
- [ ] Ports: HTTP(80), HTTPS(443), SSH(22), FTP(21), DNS(53), SMTP(25), Telnet(23)
- [ ] Ethernet: half-duplex collisions, jam signal, backoff, retransmit
- [ ] Switches: **increase collision domains** (each port isolated)
- [ ] Firewall: stops unauthorized access
- [ ] Secure channel: SSH (remote shell), SSL (web)
- [ ] HTTP request: **request line + header** (+ optional body)

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| **OSI layers bottom→top** | "**P**lease **D**o **N**ot **T**hrow **S**ausage **P**izza **A**way" — Physical, Data Link, Network, Transport, Session, Presentation, Application |
| **TCP/IP layers** | "**A**ll **T**hings **I**nternet **N**etwork" — App, Transport, Internet, Network Access |
| **PDU bottom→top** | "**B**its **F**rame **P**ackets **S**egment" — "**B**ig **F**riendly **P**uppies **S**nuggle" |
| **Switch forwarding** | "Switch **M**atches **M**AC" — matches destination MAC to table |
| **LLC job** | "**L**ogical **L**ink = **L**ayer **C**onnector" — identifies network protocols |
| **Hub vs Switch** | "**H**ub = **H**alf-wit (no filtering), **S**witch = **S**mart (filters by MAC)" |
| **Cross-over** | "Cross = **C**onnect **C**ommon (same device types)" |
| **ACL implicit deny** | "**D**eny at the **D**oor (end)" |
| **TCP vs UDP** | "**T**CP = **T**rustworthy; **U**DP = **U**nreliable & **U**rgent" |
| **Port 22 SSH** | "**22** = two swans singing **Shhh**" |
| **Collision after** | "Collide → **J**am → **B**ackoff → **R**etry" — J-B-R |

## 1-Page Cram Sheet

```
OSI MODEL (bottom→top)
═══════════════════════
7 Application  ┐
6 Presentation  │→ Data
5 Session      ┘
4 Transport      → Segment    (TCP/UDP)
3 Network        → Packet     (Routing, IP)
2 Data Link      → Frame      (MAC, LLC, Switch)
1 Physical       → Bit        (Hub, Repeater)

TCP/IP: Application | Transport | Internet | Network Access

PDU bottom→top: Bit → Frame → Packet → Segment

KEY DEVICES
═══════════
Hub      → L1, broadcasts, NO filtering
Switch   → L2, MAC table, increases collision domains
Router   → L3, routing, path selection, addressing
Firewall → Stops unauthorized access

CABLES: Cross-over (same type) vs Straight-through (diff type)

IP ADDRESSING
═════════════
Class A: 1-126   /8
Class B: 128-191 /16
Class C: 192-223 /24

Subnet: Network (all 0s) → Broadcast (all 1s) → hosts in between

PORTS
═════
HTTP=80, HTTPS=443, SSH=22, FTP=21
DNS=53, SMTP=25, Telnet=23

PROTOCOLS
═════════
TCP: reliable, connection-oriented, ordered
UDP: fast, connectionless, unordered

ACL: sequential, implicit deny at end

COLLISION: send → collide → jam → backoff → retry

HTTP request: request line + header
```
