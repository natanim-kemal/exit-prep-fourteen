# Fundamentals of Networking — Study Notes

## 1. OSI Model (7 Layers)

| Layer | Function | Example Protocols |
|-------|----------|-----------------|
| 7. Application | User interface, network services | HTTP, FTP, SMTP, DNS |
| 6. Presentation | Data translation, encryption, compression | SSL/TLS, JPEG, ASCII |
| 5. Session | Session management, dialog control | NetBIOS, RPC |
| 4. Transport | End-to-end connection, reliability | TCP, UDP |
| 3. Network | Logical addressing, routing | IP, ICMP, ARP, RIP, OSPF |
| 2. Data Link | Framing, MAC addressing, error detection | Ethernet, PPP, Wi-Fi |
| 1. Physical | Bit transmission, electrical signals | Cables, hubs, repeaters |

**Presentation layer functions**: encryption, compression, translation. **Synchronization** is NOT a presentation layer function (it belongs to Session layer).

## 2. TCP/IP Model (4 Layers)

1. **Application** (HTTP, FTP, SMTP, DNS)
2. **Transport** (TCP — reliable, connection-oriented; UDP — fast, connectionless)
3. **Internet/Network** (IP — logical addressing, routing)
4. **Network Access/Link** (Ethernet, Wi-Fi, physical medium)

**TCP provides**: reliable data delivery, flow control, congestion control, error checking, sequencing.

**Flow control**: prevents sender from overwhelming receiver by controlling data transmission rate.

## 3. Network Topologies

| Topology | Description | Advantage | Disadvantage |
|----------|------------|-----------|-------------|
| **Bus** | Single cable, all nodes connected | Simple, cheap | Single point of failure |
| **Star** | Central hub/switch, all nodes connect to it | Easy to manage | Hub failure = network down |
| **Ring** | Nodes connected in a circle | Equal access | Single break breaks network |
| **Mesh** | Every node connected to every other | High redundancy, fault-tolerant | Expensive, complex |
| **Hybrid** | Combination of topologies | Flexible, scalable | Complex design |
| **Tree** | Hierarchical star-bus hybrid | Scalable | Root failure affects all |

**Mesh topology** provides minimal latency and high redundancy (best for mission-critical networks requiring fault tolerance).

## 4. IP Addressing & Subnetting

**IPv4**: 32-bit address (4 octets), e.g., 192.168.1.1. Classes A-E.
**IPv6**: 128-bit address, solves IPv4 exhaustion.
**Subnet mask**: determines network vs host portion (e.g., 255.255.255.0 = /24).
**CIDR notation**: 192.168.1.0/24.

**Private IP ranges**: 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16.
**NAT (Network Address Translation)**: maps private IPs to public IP for internet access.

## 5. Routing Protocols

- **RIP (Routing Information Protocol)**: distance-vector, hop count metric, max 15 hops
- **OSPF (Open Shortest Path First)**: link-state, uses Dijkstra algorithm, faster convergence
- **BGP (Border Gateway Protocol)**: exterior gateway protocol used between autonomous systems

## 6. Network Devices

| Device | Layer | Function |
|--------|-------|----------|
| **Hub** | Physical (L1) | Repeats signal to all ports |
| **Switch** | Data Link (L2) | Forwards frames using MAC addresses |
| **Router** | Network (L3) | Routes packets between networks using IP addresses |
| **Bridge** | Data Link (L2) | Connects two network segments |
| **Gateway** | All layers | Connects different network architectures/protocols |
| **Firewall** | Network-Application | Filters traffic based on security rules |

## 7. Network Security

- **Firewall types**: Packet Filtering (L3/L4), Stateful Inspection (tracks connections), Proxy (L7, acts as intermediary), Cloud-Based, Next-Gen
- **Stateful Inspection Firewall**: tracks active connections and allows only legitimate traffic
- **VPN (Virtual Private Network)**: creates encrypted tunnel over public internet
- **IDS/IPS (Intrusion Detection/Prevention System)**: monitors for malicious activity

## 8. Key Protocols

- **HTTP**: port 80, request-response, stateless. HTTP message structure: request line / status line + headers + optional body (no specified minimum size).
- **HTTPS**: port 443, HTTP over SSL/TLS
- **FTP**: port 21 (control), 20 (data) — file transfer
- **DNS**: port 53, resolves domain names to IP addresses
- **DHCP**: dynamically assigns IP addresses
- **SMTP**: port 25, email transmission
- **SNMP**: network management and monitoring
