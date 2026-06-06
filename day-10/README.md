# Day 10 — Fundamentals of Networking (8 Items)

## Files in this directory

| File | Content |
|------|---------|
| `01-networking-complete.md` | Full theory: LAN/WAN/MAN/PAN, topologies, OSI 7 layers with PDU order, TCP/IP 4 layers, TCP vs UDP, LLC sublayer, devices (hub/switch/router/firewall), IPv4 classes & subnetting, ACLs, Ethernet collisions, cross-over vs straight-through, ports & protocols + 16 exam Q&As |
| `02-trace-exercises.md` | 20 exam-style problems: OSI layer identification, PDU ordering, device-to-layer mapping, switch forwarding trace, hub vs switch collision domains, cable selection, subnetting, valid host check, ACL trace, collision trace, port matching |
| `03-review-checklist.md` | Mastery checklist by LO, mnemonics, 1-page cram sheet |

## How to use today

1. **Read** `01-networking-complete.md` (2.5 hrs) — focus on: OSI PDU order (Bit→Frame→Packet→Segment), TCP/IP Internet layer = routing, LLC sublayer function, switching (MAC address table), switch vs hub collision domains, valid host subnetting, ACL implicit deny
2. **Practice** `02-trace-exercises.md` (1.5 hrs) — especially PDU ordering, subnetting calculations, ACL trace
3. **Self-test** `03-review-checklist.md` (30 min)

## Key exam focus (from 18 actual questions extracted)

- **OSI PDU order bottom→top**: Bit → Frame → Packet → Segment — AAU 2015
- **TCP/IP Internet layer**: addressing, path selection, routing — AAU 2015
- **SSH port**: 22 — moee Q34 (also in Day 6)
- **Switch forwarding**: matches destination MAC to MAC table — moee Q5
- **LLC sublayer**: identifies Network layer protocols — moee Q51
- **OSPF is NOT data link**: OSPF is Network layer routing protocol — moee Q58
- **Hub cannot filter**: switches increase collision domains — AAU 2015 Q5
- **Collision**: jam signal → backoff → retransmit — AAU 2015
- **Cross-over NOT for**: switch to PC — AAU 2015
- **Firewall purpose**: stop unauthorized access — AAU 2015
- **Application layer**: process-to-process interaction — moee Q28
- **ACL implicit deny** at end — moee Q7
- **Valid host in /21 subnet**: broadcast address is NOT valid — AAU 2015
- **HTTP request**: request line + header — AAU 2015
- **SSH secure channel**: standards and protocol for secure remote connection — AAU 2015

## Source mapping
| Exam File | Networking Questions Found |
|-----------|-------------------------|
| Model moee.docx | 7 questions |
| AAU Exit Exam 2015.docx | 11 questions |
| **Total** | **18 questions** |

## Next: Day 11 — Software & Information Security (6 items)
