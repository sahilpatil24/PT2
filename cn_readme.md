# Computer Networks: PT2 Question Bank (2026)

Source file: `Question_Bank_for_PT2_2026.pdf`
Applies to: C1, C2, C3

Solutions (5 marks each) are at the bottom: [Go to Solutions Index](#solutions-index)

This README organizes the PT2 question bank by topic so it is easier to study from. Question numbers match the original PDF.

> Note from the question bank: problems can be asked on the header formats of various protocols and on IPv4 subnetting.

---

## 1. Network Layer: IPv4 Addressing

| Q No. | Topic |
|-------|-------|
| [Q1](#q1) | Explain in detail: (a) IPv4 classful addressing, (b) IPv4 classless addressing, (c) Supernetting, (d) Subnetting (fixed and variable size) |
| [Q2](#q2) | Design problems and numericals on classful/classless subnetting and supernetting |

## 2. Network Layer: Protocols (IPv4, IPv6, ARP, ICMP)

| Q No. | Topic |
|-------|-------|
| [Q3](#q3) | IPv4 protocol with its header format |
| [Q4](#q4) | IPv6 with examples |
| [Q5](#q5) | (a) ARP, (b) ICMP |

## 3. Routing Algorithms

| Q No. | Topic |
|-------|-------|
| [Q6](#q6) | With examples: (a) Distance vector routing, (b) Link state routing |
| [Q7](#q7) | Count to infinity problem in distance vector routing |

## 4. Congestion Control and Traffic Shaping

| Q No. | Topic |
|-------|-------|
| [Q8](#q8) | Token bucket and leaky bucket algorithms with example |
| [Q10](#q10) | Open loop and closed loop congestion control |
| [Q15](#q15) | Congestion control in TCP: (i) Slow start, (ii) Additive Increase/Multiplicative Decrease (AIMD) |
| [Q16](#q16) | Congestion avoidance techniques: (ii) DECbit, (iii) RED |

## 5. Transport Layer (TCP, UDP)

| Q No. | Topic |
|-------|-------|
| [Q9](#q9) | Header formats of TCP and UDP |
| [Q13](#q13) | TCP three-way handshake: connection establishment and connection release, with neat diagrams |
| [Q14](#q14) | Flow control mechanism in TCP |

## 6. Application Layer

| Q No. | Topic |
|-------|-------|
| [Q11](#q11) | (a) DNS, (b) FTP, (c) Telnet, (d) HTTP |

## 7. Security and Modern Networks

| Q No. | Topic |
|-------|-------|
| [Q17](#q17) | Purpose of encryption and authentication in SSH communication |
| [Q18](#q18) | Main components of 5G network architecture and their roles |
| [Q19](#q19) | How phishing attacks exploit human vulnerabilities to gain unauthorized access to sensitive information |

## 8. Comparison Questions (Q12)

Include header formats where applicable.

| Part | Comparison |
|------|------------|
| [a](#q12a) | IPv4 vs IPv6 |
| [b](#q12b) | TCP vs UDP vs SCTP |
| [c](#q12c) | Token bucket vs Leaky bucket |
| [d](#q12d) | Open loop vs Closed loop congestion control |
| [e](#q12e) | HTTP vs FTP |

---

## Header Formats to Prepare

Since the note says problems can be asked on header formats, make sure you can draw and explain the fields of:

- IPv4 header (Q3)
- IPv6 header (Q4, Q12a)
- TCP header (Q9, Q12b)
- UDP header (Q9, Q12b)
- SCTP (for the comparison in Q12b)

## Numericals to Practice

- Classful subnetting (Q2)
- Classless subnetting (Q2)
- Fixed-size and variable-size subnetting (Q1d, Q2)
- Supernetting (Q1c, Q2)
- Token bucket and leaky bucket examples (Q8)

## Study Checklist

- [ ] [Q1](#q1): IPv4 classful, classless, supernetting, subnetting
- [ ] [Q2](#q2): Subnetting and supernetting numericals
- [ ] [Q3](#q3): IPv4 header format
- [ ] [Q4](#q4): IPv6 with examples
- [ ] [Q5](#q5): ARP and ICMP
- [ ] [Q6](#q6): Distance vector and link state routing
- [ ] [Q7](#q7): Count to infinity problem
- [ ] [Q8](#q8): Token and leaky bucket
- [ ] [Q9](#q9): TCP and UDP headers
- [ ] [Q10](#q10): Open loop and closed loop congestion
- [ ] [Q11](#q11): DNS, FTP, Telnet, HTTP
- [ ] [Q12](#q12): All five comparisons (a to e)
- [ ] [Q13](#q13): TCP three-way handshake and release
- [ ] [Q14](#q14): TCP flow control
- [ ] [Q15](#q15): TCP slow start and AIMD
- [ ] [Q16](#q16): DECbit and RED
- [ ] [Q17](#q17): SSH encryption and authentication
- [ ] [Q18](#q18): 5G architecture components
- [ ] [Q19](#q19): Phishing attacks


---

<a id="solutions"></a>

# Solutions (5 marks each)

<a id="solutions-index"></a>

## Solutions Index

**Network Layer: IPv4 Addressing**
[Q1 Classful, Classless, Supernetting, Subnetting](#q1) | [Q2 Numericals](#q2)

**Network Layer: Protocols**
[Q3 IPv4 Header](#q3) | [Q4 IPv6](#q4) | [Q5 ARP and ICMP](#q5)

**Routing**
[Q6 Distance Vector and Link State](#q6) | [Q7 Count to Infinity](#q7)

**Congestion Control and Traffic Shaping**
[Q8 Token and Leaky Bucket](#q8) | [Q10 Open and Closed Loop](#q10) | [Q15 Slow Start and AIMD](#q15) | [Q16 DECbit and RED](#q16)

**Transport Layer**
[Q9 TCP and UDP Headers](#q9) | [Q13 Three-Way Handshake and Release](#q13) | [Q14 TCP Flow Control](#q14)

**Application Layer**
[Q11 DNS, FTP, Telnet, HTTP](#q11)

**Security and Modern Networks**
[Q17 SSH](#q17) | [Q18 5G Architecture](#q18) | [Q19 Phishing](#q19)

**Comparisons**
[Q12 all parts](#q12): [a IPv4 vs IPv6](#q12a) | [b TCP vs UDP vs SCTP](#q12b) | [c Token vs Leaky](#q12c) | [d Open vs Closed Loop](#q12d) | [e HTTP vs FTP](#q12e)

[Back to top of README](#computer-networks-pt2-question-bank-2026)

---

<a id="q1"></a>

## Q1) IPv4 addressing: classful, classless, supernetting, subnetting

[Back to index](#solutions-index)

<a id="q1a"></a>

### a) IPv4 classful addressing

An IPv4 address is 32 bits long, written in dotted decimal (for example 192.168.1.10). In classful addressing the address space is divided into five fixed classes. Each address has a **netid** (network part) and a **hostid** (host part), and the class decides where the split falls.

| Class | First bits | First octet range | Default mask | Netid / Hostid bits | Hosts per network |
|-------|-----------|-------------------|--------------|---------------------|-------------------|
| A | 0 | 1 to 126 | 255.0.0.0 (/8) | 8 / 24 | 2^24 - 2 = 16,777,214 |
| B | 10 | 128 to 191 | 255.255.0.0 (/16) | 16 / 16 | 2^16 - 2 = 65,534 |
| C | 110 | 192 to 223 | 255.255.255.0 (/24) | 24 / 8 | 2^8 - 2 = 254 |
| D | 1110 | 224 to 239 | not applicable | Multicast | not applicable |
| E | 1111 | 240 to 255 | not applicable | Reserved for research | not applicable |

Points to remember:

- Two addresses in every network are reserved: the network address (all host bits 0) and the directed broadcast address (all host bits 1). That is why hosts = 2^n - 2.
- 127.x.x.x is loopback, 0.0.0.0 means "this host", and 255.255.255.255 is limited broadcast.
- The class is identified from the first octet, so no mask needs to be sent.
- **Drawback:** address wastage. A company needing 500 hosts must take a Class B (65,534 addresses) because Class C is too small. This led to CIDR.

<a id="q1b"></a>

### b) IPv4 classless addressing (CIDR)

Classless Inter-Domain Routing removes the fixed classes. An address is written as **a.b.c.d/n**, where n is the length of the network prefix in bits. The prefix can be any length from 0 to 32, so blocks can be sized to actual need.

Rules for a valid CIDR block:

1. The addresses must be contiguous.
2. The number of addresses must be a power of 2 (2^(32 - n)).
3. The first address must be divisible by the block size.

Example: 192.168.8.0/22

- Mask = 255.255.252.0
- Addresses in block = 2^10 = 1024, usable hosts = 1022
- Range: 192.168.8.0 to 192.168.11.255 (network address 192.168.8.0, broadcast 192.168.11.255)

Advantages: efficient use of address space, smaller routing tables through route aggregation, and flexibility for ISPs.

<a id="q1c"></a>

### c) Supernetting

Supernetting combines several contiguous smaller networks (for example Class C) into one larger network. The mask becomes **shorter** than the default mask. It is used to reduce the size of routing tables.

Conditions:

- The networks must be contiguous.
- The number of networks must be a power of 2.
- The first network address must be divisible by the total block size (so the third octet of the first network is divisible by the number of networks being combined).

Example: combine 200.1.0.0, 200.1.1.0, 200.1.2.0 and 200.1.3.0 (four Class C networks).

- 4 = 2^2, so 2 bits are borrowed from the network part: /24 becomes /22.
- Supernet = 200.1.0.0/22, mask 255.255.252.0, total addresses 1024.

<a id="q1d"></a>

### d) Subnetting (fixed and variable size)

Subnetting divides one network into smaller sub-networks by **borrowing bits from the host part**, so the mask becomes longer.

**Fixed Length Subnet Masking (FLSM):** all subnets have the same size and the same mask.

- Example: divide 192.168.1.0/24 into 4 subnets. 2 bits are borrowed, so the mask is /26 (255.255.255.192). Each subnet has 64 addresses (62 hosts).
- Subnets: 192.168.1.0, 192.168.1.64, 192.168.1.128, 192.168.1.192.
- Drawback: wastage, because every subnet is as large as the largest need.

**Variable Length Subnet Masking (VLSM):** subnets have different sizes and different masks, allocated according to requirement.

- Method: sort requirements from largest to smallest, give each the smallest power-of-2 block that fits, and allocate one after another.
- Example: 192.168.1.0/24 with A = 100 hosts, B = 50, C = 20. A gets /25 (192.168.1.0 to .127), B gets /26 (.128 to .191), C gets /27 (.192 to .223).

Benefits: less wastage, and it supports hierarchical addressing.

---

<a id="q2"></a>

## Q2) Design problems and numericals (subnetting and supernetting)

[Back to index](#solutions-index)

Quick formulas:

- Bits to borrow for S subnets: smallest n such that 2^n >= S.
- Hosts per subnet = 2^h - 2 (h = remaining host bits).
- Block size = 256 - (value of the last non-255 octet of the mask).
- Network address = IP AND mask. Broadcast = network address with all host bits set to 1.

### Type 1: Fixed-size subnetting (classful)

**Example 1.** Class C network 192.168.10.0. Create 6 subnets.

- 2^3 = 8 >= 6, so borrow 3 bits. Mask = /27 = 255.255.255.224. Block size = 32. Hosts per subnet = 2^5 - 2 = 30.

| Subnet | Network | Usable range | Broadcast |
|--------|---------|--------------|-----------|
| 1 | 192.168.10.0 | .1 to .30 | 192.168.10.31 |
| 2 | 192.168.10.32 | .33 to .62 | 192.168.10.63 |
| 3 | 192.168.10.64 | .65 to .94 | 192.168.10.95 |
| 4 | 192.168.10.96 | .97 to .126 | 192.168.10.127 |
| 5 | 192.168.10.128 | .129 to .158 | 192.168.10.159 |
| 6 | 192.168.10.160 | .161 to .190 | 192.168.10.191 |

(Subnets 7 and 8 at .192 and .224 are left unused.)

**Example 2.** Class B network 130.10.0.0. Create 5 subnets.

- 2^3 = 8 >= 5, so borrow 3 bits. Mask = /19 = 255.255.224.0. Block size = 32 in the third octet. Hosts = 2^13 - 2 = 8190.
- Subnet networks: 130.10.0.0, 130.10.32.0, 130.10.64.0, 130.10.96.0, 130.10.128.0.
- For 130.10.32.0: range 130.10.32.1 to 130.10.63.254, broadcast 130.10.63.255.

### Type 2: Classless (CIDR) address details

**Example 1.** Given 200.10.20.77/28, find network, broadcast, range and hosts.

- Mask /28 = 255.255.255.240. Block size = 16. 77 lies in the block starting at 64 (64 to 79).
- Network = 200.10.20.64. Broadcast = 200.10.20.79. Range = 200.10.20.65 to 200.10.20.78. Hosts = 2^4 - 2 = 14.

**Example 2.** Given 10.1.1.130/25.

- Mask = 255.255.255.128. Block size = 128. 130 lies in the block 128 to 255.
- Network = 10.1.1.128. Broadcast = 10.1.1.255. Range = 10.1.1.129 to 10.1.1.254. Hosts = 126.

### Type 3: Variable-size subnetting (VLSM)

**Example 1.** Network 192.168.1.0/24. Departments need 100, 50, 20 and 10 hosts.

| Dept | Need | Block | Mask | Network | Range | Broadcast |
|------|------|-------|------|---------|-------|-----------|
| A | 100 | 128 | /25 | 192.168.1.0 | .1 to .126 | .127 |
| B | 50 | 64 | /26 | 192.168.1.128 | .129 to .190 | .191 |
| C | 20 | 32 | /27 | 192.168.1.192 | .193 to .222 | .223 |
| D | 10 | 16 | /28 | 192.168.1.224 | .225 to .238 | .239 |

**Example 2.** Network 172.16.5.0/24. Three LANs need 60, 30 and 12 hosts, plus two point-to-point WAN links (2 hosts each).

| Segment | Need | Mask | Network | Range | Broadcast |
|---------|------|------|---------|-------|-----------|
| LAN1 | 60 | /26 | 172.16.5.0 | .1 to .62 | .63 |
| LAN2 | 30 | /27 | 172.16.5.64 | .65 to .94 | .95 |
| LAN3 | 12 | /28 | 172.16.5.96 | .97 to .110 | .111 |
| WAN1 | 2 | /30 | 172.16.5.112 | .113 to .114 | .115 |
| WAN2 | 2 | /30 | 172.16.5.116 | .117 to .118 | .119 |

### Type 4: Supernetting

**Example 1.** Combine 198.10.4.0, 198.10.5.0, 198.10.6.0, 198.10.7.0 (Class C).

- 4 networks, so 2 bits. Third octet of the first network is 4, divisible by 4, so it is valid.
- Supernet = 198.10.4.0/22, mask 255.255.252.0, range 198.10.4.0 to 198.10.7.255 (1024 addresses).
- Note: 198.10.5.0 to 198.10.8.0 could **not** be combined, because 5 is not divisible by 4.

**Example 2.** Combine 8 Class C networks starting at 192.24.0.0.

- 8 = 2^3, so 3 bits. First third octet 0 is divisible by 8, so it is valid.
- Supernet = 192.24.0.0/21, mask 255.255.248.0, range 192.24.0.0 to 192.24.7.255 (2048 addresses).

---

<a id="q3"></a>

## Q3) IPv4 protocol and header format

[Back to index](#solutions-index)

IPv4 is the network layer protocol of the Internet. It is **connectionless, unreliable and best-effort**: it delivers datagrams but gives no guarantee of delivery, ordering or error recovery (these are left to upper layers). It provides addressing, routing and fragmentation.

```
 0        4        8               16   19                          31
+--------+--------+----------------+----+---------------------------+
|Version |  IHL   | DSCP/ToS (8)   |        Total Length (16)       |
+--------+--------+----------------+----+---------------------------+
|        Identification (16)       |Flag| Fragment Offset (13)      |
+-------------------+--------------+----+---------------------------+
|    TTL (8)        |  Protocol (8)|      Header Checksum (16)      |
+-------------------+--------------+--------------------------------+
|                    Source IP Address (32)                         |
+-------------------------------------------------------------------+
|                  Destination IP Address (32)                      |
+-------------------------------------------------------------------+
|                    Options (variable) + Padding                   |
+-------------------------------------------------------------------+
```

| Field | Size | Purpose |
|-------|------|---------|
| Version | 4 bits | IP version, value 4 |
| IHL | 4 bits | Header length in 32-bit words (min 5, so 20 bytes; max 15, so 60 bytes) |
| DSCP / ToS | 8 bits | Type of service, priority and QoS |
| Total Length | 16 bits | Header plus data, in bytes (max 65,535) |
| Identification | 16 bits | Identifies fragments of the same datagram |
| Flags | 3 bits | Reserved, DF (Don't Fragment), MF (More Fragments) |
| Fragment Offset | 13 bits | Position of the fragment in the original datagram, in units of 8 bytes |
| TTL | 8 bits | Hop limit, decremented at each router, packet discarded at 0 |
| Protocol | 8 bits | Upper layer protocol (1 = ICMP, 6 = TCP, 17 = UDP) |
| Header Checksum | 16 bits | Error check on the header only |
| Source / Destination Address | 32 bits each | Sender and receiver IP |
| Options | 0 to 40 bytes | Record route, timestamp, security and so on |

---

<a id="q4"></a>

## Q4) IPv6 with examples

[Back to index](#solutions-index)

IPv6 is the successor to IPv4, designed to solve address exhaustion. Addresses are **128 bits**, written as eight groups of four hexadecimal digits separated by colons, giving about 3.4 x 10^38 addresses.

**Address notation and shortening rules**

1. Leading zeros in a group can be dropped.
2. One run of consecutive all-zero groups can be replaced by `::` (only once per address).

Example:

- Full: `2001:0db8:0000:0000:0000:ff00:0042:8329`
- Short: `2001:db8::ff00:42:8329`
- Loopback: `::1`. Link-local: `fe80::/10`. Unspecified: `::`.

**Address types**

| Type | Description | Example |
|------|-------------|---------|
| Unicast | One sender to one receiver | 2001:db8::1 |
| Multicast | One to a group (prefix ff00::/8) | ff02::1 (all nodes on link) |
| Anycast | One to the nearest of a group of interfaces | assigned from the unicast space |

There is no broadcast in IPv6; multicast replaces it.

**Header (fixed 40 bytes)**

```
+---------+---------------+------------------------------+
| Ver (4) | Traffic Class | Flow Label (20)              |
|         | (8)           |                              |
+---------+---------------+---------+----------+---------+
| Payload Length (16)     | Next    | Hop Limit (8)      |
|                         | Hdr (8) |                    |
+-------------------------+---------+--------------------+
|              Source Address (128)                      |
+--------------------------------------------------------+
|            Destination Address (128)                   |
+--------------------------------------------------------+
```

- **Traffic Class:** priority. **Flow Label:** identifies packets of one flow for special handling.
- **Payload Length:** size of data after the header. **Next Header:** next extension header or upper layer protocol (like the IPv4 Protocol field). **Hop Limit:** replaces TTL.

**Key features:** larger address space, simpler fixed header (no checksum, no router fragmentation), extension headers, stateless autoconfiguration, built-in IPsec support, better multicast and QoS.

**Transition from IPv4:** dual stack, tunneling (IPv6 packets inside IPv4), and header translation.

---

<a id="q5"></a>

## Q5) ARP and ICMP

[Back to index](#solutions-index)

<a id="q5a"></a>

### a) ARP (Address Resolution Protocol)

ARP maps a known **IP address to the MAC (physical) address** of a device on the same local network. It is needed because frames on a LAN are delivered using MAC addresses.

Working:

1. Host A wants to send to host B (IP known, MAC unknown) and first checks its **ARP cache**.
2. If not found, A **broadcasts an ARP request**: "Who has IP B? Tell A."
3. Every host receives it, but only B replies with a **unicast ARP reply** containing its MAC address.
4. A stores the mapping in its cache and sends the frame.

If the destination is on a different network, the host ARPs for the **default gateway's** MAC instead.

ARP packet fields: Hardware type, Protocol type, Hardware length, Protocol length, Operation (1 = request, 2 = reply), Sender hardware address, Sender IP, Target hardware address, Target IP.

Related: Proxy ARP (a router answers on behalf of another host), Gratuitous ARP (announces or checks own address), and RARP (MAC to IP, now obsolete).

<a id="q5b"></a>

### b) ICMP (Internet Control Message Protocol)

ICMP works at the network layer alongside IP (IP protocol number 1). Since IP has no error reporting, ICMP is used to **report errors and send diagnostic or query messages**. It does not correct errors; it only reports them to the source.

Message header: Type (8 bits), Code (8 bits), Checksum (16 bits), followed by data. For error messages the data contains the original IP header plus the first 8 bytes of the datagram that caused the error.

| Category | Message | Type |
|----------|---------|------|
| Error reporting | Destination unreachable | 3 |
| | Time exceeded (TTL = 0 or reassembly timeout) | 11 |
| | Parameter problem | 12 |
| | Redirect (a better route exists) | 5 |
| Query | Echo request / Echo reply | 8 / 0 |
| | Timestamp request / reply | 13 / 14 |

Uses: **ping** uses echo request and reply; **traceroute** uses increasing TTL values and the Time Exceeded replies to discover the path.

---

<a id="q6"></a>

## Q6) Routing algorithms with example

[Back to index](#solutions-index)

<a id="q6a"></a>

### a) Distance Vector Routing (DVR)

Each router knows the distance (cost) to every destination and the next hop, and periodically **shares its whole routing table only with its direct neighbours**. It uses the **Bellman-Ford equation**:

d_x(y) = min over neighbours v of { c(x, v) + d_v(y) }

Steps:

1. Each router starts with distance 0 to itself, the link cost to neighbours, and infinity for the rest.
2. Each router sends its vector to its neighbours.
3. On receiving a vector, a router updates any entry where going through that neighbour is cheaper.
4. This repeats until no table changes (convergence).

Example: A - B cost 2, B - C cost 3, A - C cost 7.

| Router A | Initial | After exchange |
|----------|---------|----------------|
| to B | 2 (B) | 2 (B) |
| to C | 7 (C) | min(7, 2 + 3) = **5 via B** |

Similarly C updates to A as 5 via B. RIP is a DVR protocol (metric is hop count, max 15).

<a id="q6b"></a>

### b) Link State Routing (LSR)

Each router learns the **full topology** and then independently computes the best path using **Dijkstra's algorithm**.

Steps:

1. **Discover neighbours** by exchanging Hello packets.
2. **Measure the cost** of each link.
3. **Build a Link State Packet (LSP)** listing neighbours and costs.
4. **Flood** the LSP to all routers in the area.
5. Each router builds the link state database and runs **Dijkstra** to compute the shortest path tree, then fills its routing table.

Example: links A-B = 2, A-C = 5, B-C = 1, B-D = 4, C-D = 2. Dijkstra from A:

| Step | Permanent set | Cost to B | Cost to C | Cost to D |
|------|---------------|-----------|-----------|-----------|
| 1 | A | 2 | 5 | infinity |
| 2 | A, B | 2 | 3 (via B) | 6 (via B) |
| 3 | A, B, C | 2 | 3 | 5 (via C) |
| 4 | A, B, C, D | 2 | 3 | 5 |

Result for A: B via B (2), C via B (3), D via B then C (5). OSPF is an LSR protocol.

Key difference: DVR shares knowledge of the whole network with neighbours only; LSR shares knowledge of neighbours with the whole network.

---

<a id="q7"></a>

## Q7) Count to infinity problem in DVR

[Back to index](#solutions-index)

DVR converges quickly on **good news** (a new or cheaper route) but slowly on **bad news** (a link failure). Routers keep trusting each other's stale information, so a route cost keeps increasing.

Example: A - B - C in a line, each link cost 1. B reaches C with cost 1 and A reaches C with cost 2 (via B).

Now the **B-C link fails**.

| Round | B's cost to C | A's cost to C | What happened |
|-------|---------------|---------------|---------------|
| 0 | infinity | 2 | B sees the link is down |
| 1 | 3 (via A) | 2 | B hears from A "C is 2 away" and believes it, not knowing A's route goes through B |
| 2 | 3 | 4 (via B) | A hears B's new cost 3, so 3 + 1 = 4 |
| 3 | 5 (via A) | 4 | B updates 4 + 1 |
| 4 | 5 | 6 (via B) | and so on |

The costs keep increasing until they reach the value defined as infinity (16 in RIP). Meanwhile a routing loop exists between A and B, and packets for C bounce between them.

**Solutions**

- **Define a small maximum for infinity** (RIP uses 16) so counting stops quickly.
- **Split horizon:** a router does not advertise a route back out of the interface it learned it from (B would not tell A about C).
- **Split horizon with poison reverse:** it does advertise the route back, but with cost infinity.
- **Hold-down timers:** after a route goes down, ignore worse updates for a period.
- **Triggered updates:** send an update immediately when a route changes.

Split horizon does not fully solve loops involving three or more routers, which is why the other methods are also used.

---

<a id="q8"></a>

## Q8) Token bucket and leaky bucket algorithms

[Back to index](#solutions-index)

Both are **traffic shaping** (open loop) algorithms that regulate the rate at which data enters the network.

### Leaky bucket

- Packets enter a bucket of finite capacity, and the bucket leaks (sends out) at a **constant rate**, whatever the input rate.
- If the bucket is full, arriving packets are **discarded**.
- Effect: bursty input becomes smooth, constant output.

Example: bucket capacity = 6 packets, leak rate = 3 packets per second.

| Second | Arrivals | In bucket after arrival | Sent | Left | Dropped |
|--------|----------|-------------------------|------|------|---------|
| 1 | 5 | 5 | 3 | 2 | 0 |
| 2 | 4 | 6 | 3 | 3 | 0 |
| 3 | 0 | 3 | 3 | 0 | 0 |
| 4 | 8 | 6 (capacity) | 3 | 3 | 2 |

### Token bucket

- Tokens are added to a bucket at a **fixed rate** (r tokens per second) up to a maximum capacity b.
- To send a packet the host must **consume a token**. Packets that find no token wait (or are dropped by policy).
- **Idle time saves tokens**, so a host can later send a **burst** up to b packets, and the long-term average rate stays at r.

Example: token rate = 2 per second, bucket capacity = 5 (starts full). A burst of 8 packets arrives at t = 0.

- t = 0: 5 tokens, so 5 packets are sent, and 3 wait.
- t = 1: 2 new tokens, so 2 more packets are sent, and 1 waits.
- t = 2: 2 new tokens, so the last packet is sent, and 1 token is left.

Summary: the leaky bucket enforces a rigid output rate, while the token bucket allows controlled bursts.

---

<a id="q9"></a>

## Q9) Header format of TCP and UDP

[Back to index](#solutions-index)

### TCP header (20 to 60 bytes)

```
 0                16                31
+-----------------+-----------------+
| Source Port     | Destination Port|
+-----------------+-----------------+
|         Sequence Number (32)      |
+-----------------------------------+
|     Acknowledgement Number (32)   |
+------+-----+-----+----------------+
|Offset|Rsvd |Flags| Window Size    |
+------+-----+-----+----------------+
| Checksum        | Urgent Pointer  |
+-----------------+-----------------+
|         Options + Padding         |
+-----------------------------------+
|               Data                |
+-----------------------------------+
```

| Field | Size | Purpose |
|-------|------|---------|
| Source / Destination Port | 16 bits each | Identify the sending and receiving application |
| Sequence Number | 32 bits | Number of the first data byte in the segment |
| Acknowledgement Number | 32 bits | Next byte the receiver expects |
| Data Offset (HLEN) | 4 bits | Header length in 32-bit words |
| Flags | 6 bits (plus ECN bits in newer versions) | URG, ACK, PSH, RST, SYN, FIN |
| Window Size | 16 bits | Receiver's available buffer, used for flow control |
| Checksum | 16 bits | Error detection over header, data and pseudo-header |
| Urgent Pointer | 16 bits | Points to the end of urgent data (valid if URG = 1) |
| Options | up to 40 bytes | MSS, window scale, timestamps, SACK |

Flag meanings: SYN opens a connection, ACK acknowledges, FIN closes, RST resets, PSH asks for immediate delivery, URG marks urgent data.

### UDP header (8 bytes)

```
 0                16                31
+-----------------+-----------------+
| Source Port     | Destination Port|
+-----------------+-----------------+
| Length          | Checksum        |
+-----------------+-----------------+
|               Data                |
+-----------------------------------+
```

- **Source and Destination Port** (16 bits each), **Length** (header plus data, 16 bits), **Checksum** (16 bits, optional in IPv4).
- UDP is connectionless and has no sequencing, acknowledgement or flow control, so the header is small and fast.

---

<a id="q10"></a>

## Q10) Open loop and closed loop congestion control

[Back to index](#solutions-index)

Congestion occurs when the load on the network exceeds its capacity, causing delay and packet loss.

### Open loop (prevention)

Policies are designed so that congestion does not happen. **No feedback** from the network is used, and decisions are made at the source or destination.

| Policy | How it prevents congestion |
|--------|----------------------------|
| Retransmission policy | Good timers avoid unnecessary retransmissions |
| Window policy | Selective Repeat sends less duplicate data than Go-Back-N |
| Acknowledgement policy | Delayed or cumulative ACKs reduce traffic |
| Discard policy | Routers drop less important packets first (for example in audio) |
| Admission policy | Refuse a new flow if resources are not available (used in virtual circuits) |

Traffic shaping (leaky bucket, token bucket) also belongs here.

### Closed loop (removal)

Congestion is **detected and then removed**, using **feedback**. Three steps: monitor the system, pass the information to where action can be taken, and adjust the operation.

| Method | Description |
|--------|-------------|
| Backpressure | A congested node stops accepting packets from its upstream node, and the pressure propagates back to the source (works in virtual circuit networks) |
| Choke packet | The congested router sends a choke packet directly to the source to slow down |
| Implicit signalling | The source guesses congestion from delayed ACKs or losses (used in TCP) |
| Explicit signalling | The router sets a bit in packets (forward or backward) to tell the source (used in DECbit, Frame Relay) |

---

<a id="q11"></a>

## Q11) DNS, FTP, Telnet, HTTP

[Back to index](#solutions-index)

<a id="q11a"></a>

### a) DNS (Domain Name System)

DNS translates human-readable **domain names to IP addresses** (for example www.example.com to 93.184.216.34). It is a distributed, hierarchical database.

- **Hierarchy:** root, then top-level domains (.com, .org, .in), then second-level (example.com), then subdomains.
- **Servers:** root servers, TLD servers, authoritative servers, and local (recursive) resolvers.
- **Resolution:** the client asks its local resolver. If not cached, the resolver queries root, then TLD, then the authoritative server (iterative), and returns the answer to the client (recursive). Results are cached with a TTL.
- **Records:** A (IPv4), AAAA (IPv6), MX (mail), NS (name server), CNAME (alias), PTR (reverse lookup).
- Uses **port 53**, UDP for queries and TCP for zone transfers and large responses.

<a id="q11b"></a>

### b) FTP (File Transfer Protocol)

FTP transfers files between a client and a server, and uses **TCP**.

- **Two connections:** a **control connection on port 21** (commands and replies, stays open for the whole session) and a **data connection on port 20** (the actual file, opened for each transfer).
- **Modes:** active (server connects back to the client) and passive (client opens both connections, works better through firewalls).
- **Commands:** USER, PASS, LIST, RETR (download), STOR (upload), QUIT.
- Data types: ASCII or binary. It requires authentication but sends everything, including passwords, in plain text (SFTP or FTPS are secure options).

<a id="q11c"></a>

### c) Telnet

Telnet provides **remote login** to another computer over a TCP connection on **port 23**. The user works as if sitting at the remote machine.

- Uses the **Network Virtual Terminal (NVT)**, a common character format, so different types of systems can interoperate.
- Options such as echo and terminal type are negotiated using DO, DON'T, WILL and WON'T commands.
- **Weakness:** all data, including the username and password, travels in plain text and can be sniffed, so it is replaced by **SSH** (Q17).

<a id="q11d"></a>

### d) HTTP (HyperText Transfer Protocol)

HTTP is the protocol of the World Wide Web, used to fetch web pages and resources. It uses **TCP, port 80** (HTTPS uses TLS on port 443).

- **Client-server, request-response model:** the browser sends a request, the server returns a response.
- **Stateless:** the server does not remember previous requests (cookies are used to maintain sessions).
- **Request:** request line (method, URL, version), headers, and optional body. **Methods:** GET, POST, PUT, DELETE, HEAD.
- **Response:** status line, headers, and body. **Status codes:** 200 OK, 301 Moved, 404 Not Found, 500 Server Error.
- HTTP/1.0 used non-persistent connections; HTTP/1.1 uses **persistent connections** by default.

---

<a id="q12"></a>

## Q12) Comparisons

[Back to index](#solutions-index)

<a id="q12a"></a>

### a) IPv4 vs IPv6

| Feature | IPv4 | IPv6 |
|---------|------|------|
| Address size | 32 bits | 128 bits |
| Notation | Dotted decimal (192.168.1.1) | Hexadecimal with colons (2001:db8::1) |
| Header size | 20 to 60 bytes (variable) | 40 bytes (fixed) |
| Header fields | 12 fields plus options | 8 fields, extension headers for options |
| Checksum | Present in header | Removed |
| Fragmentation | Source and routers | Source only |
| Broadcast | Supported | Not supported (multicast, anycast) |
| Configuration | Manual or DHCP | Auto-configuration plus DHCPv6 |
| Security | IPsec optional | IPsec built in |
| QoS | ToS field | Traffic Class and Flow Label |
| Address resolution | ARP | Neighbour Discovery (ICMPv6) |

Header comparison: IPv4 has Version, IHL, ToS, Total Length, Identification, Flags, Fragment Offset, TTL, Protocol, Checksum, Source, Destination. IPv6 has Version, Traffic Class, Flow Label, Payload Length, Next Header, Hop Limit, Source, Destination. See [Q3](#q3) and [Q4](#q4) for the diagrams.

<a id="q12b"></a>

### b) TCP vs UDP vs SCTP

| Feature | TCP | UDP | SCTP |
|---------|-----|-----|------|
| Connection | Connection-oriented | Connectionless | Connection-oriented (association) |
| Reliability | Reliable | Unreliable | Reliable |
| Data unit | Byte stream | Message (datagram) | Message-oriented |
| Ordering | In order | No ordering | Ordered or unordered, per stream |
| Multi-streaming | No | No | Yes |
| Multi-homing | No | No | Yes (multiple IP addresses per endpoint) |
| Setup | 3-way handshake | None | 4-way handshake with cookie (resists SYN flood) |
| Flow and congestion control | Yes | No | Yes |
| Header size | 20 to 60 bytes | 8 bytes | 12-byte common header plus chunks |
| Speed and overhead | Slower, more overhead | Fastest, least overhead | In between |
| Examples | HTTP, FTP, SMTP | DNS, VoIP, streaming | Signalling (SS7 over IP), telephony |

Header fields: TCP (ports, seq, ack, offset, flags, window, checksum, urgent pointer), UDP (ports, length, checksum), SCTP common header (source port, destination port, verification tag, checksum). See [Q9](#q9).

<a id="q12c"></a>

### c) Token bucket vs leaky bucket

| Feature | Leaky bucket | Token bucket |
|---------|--------------|--------------|
| Output rate | Constant | Variable (bursts allowed) |
| Bursts | Smoothed out | Allowed up to bucket size |
| Idle time | Not saved | Tokens accumulate |
| What is stored | Packets in the bucket | Tokens in the bucket |
| Packet loss | Packets dropped when bucket is full | Tokens discarded when bucket is full, packets wait or are dropped by policy |
| Flexibility | Rigid | Flexible |
| Best for | Strict constant-rate flows | Bursty traffic with an average rate limit |

<a id="q12d"></a>

### d) Open loop vs closed loop congestion control

| Feature | Open loop | Closed loop |
|---------|-----------|-------------|
| Approach | Prevention | Detection and removal |
| Feedback | None | Uses feedback from the network |
| Where applied | Source or destination | Throughout the network, adjusts the source |
| When | Before congestion occurs | After congestion is detected |
| Techniques | Retransmission, window, ACK, discard, admission policies, traffic shaping | Backpressure, choke packet, implicit and explicit signalling |
| Complexity | Simpler | More complex |

<a id="q12e"></a>

### e) HTTP vs FTP

| Feature | HTTP | FTP |
|---------|------|-----|
| Purpose | Fetch web pages and resources | Transfer files |
| Ports | 80 (443 for HTTPS) | 21 control, 20 data |
| Connections | One connection (in-band) | Two connections (control and data, out-of-band) |
| State | Stateless | Stateful (session with login) |
| Authentication | Optional | Required (username and password) |
| Connection lifetime | Short, persistent in 1.1 | Control connection lasts the session |
| Data formats | Text, HTML, images and more (MIME) | ASCII or binary |
| Commands | GET, POST, PUT, DELETE | USER, PASS, LIST, RETR, STOR |
| Speed for small files | Faster (less setup) | Slower (login overhead) |

---

<a id="q13"></a>

## Q13) TCP three-way handshake (connection establishment and release)

[Back to index](#solutions-index)

### Connection establishment (three-way handshake)

```
    Client                                  Server
      |                                       |
      |------ SYN, seq = x ------------------>|   (1) client requests connection
      |                                       |
      |<----- SYN + ACK, seq = y, ack = x+1 --|   (2) server accepts
      |                                       |
      |------ ACK, seq = x+1, ack = y+1 ----->|   (3) client confirms
      |                                       |
      |========= Connection established =====|
```

1. **SYN:** the client sends a segment with SYN = 1 and an initial sequence number x.
2. **SYN + ACK:** the server replies with SYN = 1 and ACK = 1, its own initial sequence number y, and acknowledgement number x + 1.
3. **ACK:** the client sends ACK = 1 with acknowledgement number y + 1. Data transfer can now begin.

The SYN segment consumes one sequence number. Both sides also exchange window size and MSS. The three steps synchronise the initial sequence numbers of both directions and protect against old duplicate connection requests.

### Connection release (four-way handshake)

```
    Client                                  Server
      |                                       |
      |------ FIN, seq = m ------------------>|   (1) client done sending
      |<----- ACK, ack = m+1 -----------------|   (2) server acknowledges
      |                                       |   (server may still send data: half-close)
      |<----- FIN, seq = n -------------------|   (3) server done sending
      |------ ACK, ack = n+1 ---------------->|   (4) client acknowledges
      |                                       |
      | TIME_WAIT (2 x MSL) then CLOSED       |
```

1. The client sends **FIN**.
2. The server sends **ACK**. The connection is now half-closed, and the server may still send remaining data.
3. When done, the server sends its own **FIN**.
4. The client sends the final **ACK** and waits in **TIME_WAIT** for 2 x MSL, so that the last ACK is not lost and old segments die out. The server closes on receiving the ACK.

Sometimes steps 2 and 3 are merged (FIN, then FIN + ACK, then ACK), giving a three-way release.

---

<a id="q14"></a>

## Q14) Flow control in TCP

[Back to index](#solutions-index)

Flow control makes sure a fast sender does not overwhelm a slow receiver. TCP uses a **byte-oriented sliding window** controlled by the receiver.

**Working**

- The receiver advertises its free buffer space in the **Window Size** field of every ACK. This is the **receive window (rwnd)**.
- The sender may have at most rwnd bytes of unacknowledged data outstanding. Its effective window is **min(rwnd, cwnd)**, where cwnd is the congestion window (see [Q15](#q15)).
- As the receiving application reads data, the window opens (slides right). If the buffer fills, the window shrinks.

Example: receiver buffer = 4000 bytes, MSS = 1000 bytes.

| Event | Receiver's advertised window |
|-------|------------------------------|
| Start | 4000 |
| Receives 2000 bytes, app has not read | 2000 |
| Receives 2000 more | 0 (sender must stop) |
| App reads 3000 bytes | 3000 (sender can resume) |

**Zero window:** when rwnd = 0 the sender stops and runs a **persistence timer**, sending small **window probe** segments so that a lost window-update ACK cannot cause deadlock.

**Silly window syndrome:** tiny window advertisements or tiny segments waste bandwidth.

- Sender side fix: **Nagle's algorithm** (send the first byte, then buffer until an ACK arrives or a full MSS is ready).
- Receiver side fix: **Clark's solution** (do not advertise a window until it can hold a full MSS or half the buffer) and **delayed acknowledgements**.

---

<a id="q15"></a>

## Q15) Congestion control in TCP: slow start and AIMD

[Back to index](#solutions-index)

The sender maintains a **congestion window (cwnd)** in addition to rwnd, and sends min(cwnd, rwnd). It also keeps a threshold **ssthresh**.

### i) Slow start

- Start with **cwnd = 1 MSS**.
- For each ACK received, cwnd increases by 1 MSS, so cwnd **doubles every RTT** (exponential growth).
- This continues until cwnd reaches **ssthresh**, then TCP moves to congestion avoidance (additive increase).
- On a **timeout** (severe congestion): ssthresh = cwnd / 2, cwnd = 1 MSS, and slow start restarts.

### ii) AIMD (Additive Increase / Multiplicative Decrease)

- **Additive increase:** in congestion avoidance, cwnd grows by **1 MSS per RTT** (linear growth), probing for extra bandwidth.
- **Multiplicative decrease:** when a loss is detected, cwnd is **halved**.
  - On **3 duplicate ACKs** (mild congestion): fast retransmit and fast recovery (Reno): ssthresh = cwnd / 2 and cwnd = ssthresh.
  - On **timeout** (Tahoe or Reno): cwnd = 1 MSS.
- The graph of cwnd over time forms a **sawtooth** pattern.
- AIMD is used because it converges to a **fair and efficient** sharing of bandwidth among competing flows.

Example: ssthresh = 8 MSS.

| RTT | 1 | 2 | 3 | 4 | 5 | 6 | 7 | Timeout at cwnd = 11 |
|-----|---|---|---|---|---|---|---|----------------------|
| cwnd | 1 | 2 | 4 | 8 | 9 | 10 | 11 | ssthresh = 5, cwnd = 1 |

RTT 1 to 4 is slow start (doubling). From RTT 4 (cwnd = ssthresh = 8) it is additive increase (+1 each RTT).

---

<a id="q16"></a>

## Q16) Congestion avoidance techniques: DECbit and RED

[Back to index](#solutions-index)

Congestion avoidance tries to act **before** queues overflow, by predicting congestion from the router queue length.

### ii) DECbit

The router gives **explicit feedback** using a single bit.

1. The router calculates the **average queue length** over the last busy plus idle cycle plus the current busy period.
2. If the average is **>= 1 packet**, the router sets the **congestion indication bit** in the header of packets passing through.
3. The destination copies this bit into the ACK and returns it to the source.
4. The source checks the last window of packets. If **50% or more** have the bit set, it **reduces its window multiplicatively** (to 0.875 of its value). Otherwise it **increases the window additively** by 1.

The 50% threshold is chosen because it gives good balance between throughput and delay.

### iii) RED (Random Early Detection)

The router **drops (or marks) packets randomly** as the queue starts to build, so senders slow down before the queue is full.

- It computes the weighted average queue length: **AvgLen = (1 - w) x AvgLen + w x QueueLen**, with a small weight w.
- Two thresholds, **MinThreshold** and **MaxThreshold**:

| AvgLen | Action |
|--------|--------|
| Below MinThreshold | Queue every packet, no drops |
| Between Min and Max | Drop each arriving packet with probability P that rises linearly from 0 up to MaxP |
| Above MaxThreshold | Drop every packet |

- Drop probability: **P_b = MaxP x (AvgLen - Min) / (Max - Min)**, and **P_a = P_b / (1 - count x P_b)**, where count is the number of packets queued since the last drop (this spreads drops evenly).

Advantages: avoids **global synchronisation** (many TCP flows all slowing down together), keeps the queue short, and tolerates bursts because the average is used.

---

<a id="q17"></a>

## Q17) Purpose of encryption and authentication in SSH

[Back to index](#solutions-index)

SSH (Secure Shell) provides a **secure channel over an insecure network**, on TCP **port 22**. It replaces Telnet, rlogin and FTP for remote login and file transfer (SFTP, SCP).

### Purpose of encryption

- Provides **confidentiality**: data, including passwords and commands, is unreadable to anyone sniffing the network.
- Process: client and server agree on algorithms and use a **key exchange (Diffie-Hellman)** to create a shared **session key** without sending it. All traffic is then encrypted with a fast **symmetric cipher (for example AES)**.
- A **MAC (for example HMAC-SHA2)** is attached to every packet to provide **integrity** and detect tampering or replay.

### Purpose of authentication

- **Server authentication:** the client verifies the server's **host key** (public key, checked against a known-hosts list). This prevents **man-in-the-middle** attacks and connecting to a fake server.
- **User authentication:** the server verifies who the client is, using a **password**, or better **public-key authentication** (the client proves possession of the private key by signing a challenge), or keyboard-interactive and multi-factor methods.

### SSH protocol layers

1. **Transport layer:** algorithm negotiation, key exchange, server authentication, encryption and integrity.
2. **User authentication layer:** authenticates the client.
3. **Connection layer:** multiplexes channels (shell, port forwarding, file transfer).

Together, encryption keeps the data secret and authentication makes sure both parties are who they claim to be.

---

<a id="q18"></a>

## Q18) Main components of 5G network architecture

[Back to index](#solutions-index)

The 5G system has three main parts: the **User Equipment (UE)**, the **Radio Access Network (RAN)**, and the **5G Core (5GC)**. The core uses a **service-based architecture**, where network functions (NFs) are software services that communicate with each other.

```
 UE  <--radio-->  gNB (RAN)  <--->  5G Core (AMF, SMF, UPF ...)  <--->  Data Network (Internet)
```

| Component | Role |
|-----------|------|
| **UE** | The user's device (phone, IoT device) with a SIM |
| **gNB (RAN)** | 5G base station: radio transmission, scheduling, connects UE to the core |
| **AMF** (Access and Mobility Management Function) | Registration, connection and mobility management, handover, security anchor |
| **SMF** (Session Management Function) | Sets up and manages data sessions, IP address allocation, controls the UPF |
| **UPF** (User Plane Function) | Forwards user data packets between RAN and data network, handles QoS and traffic routing |
| **AUSF** (Authentication Server Function) | Authenticates users |
| **UDM** (Unified Data Management) | Stores subscriber data and credentials |
| **PCF** (Policy Control Function) | Provides policy rules (QoS, charging) |
| **NSSF** (Network Slice Selection Function) | Selects the network slice for a user |
| **NRF** (NF Repository Function) | Lets NFs discover each other |
| **NEF / AF** | Exposes network capabilities to external applications and provides application inputs |
| **DN** | External data network such as the Internet |

Key enablers: **control and user plane separation (CUPS)**, **network slicing** (virtual networks for eMBB, URLLC, mMTC), **SDN and NFV**, massive MIMO and mmWave in the radio.

---

<a id="q19"></a>

## Q19) How phishing attacks exploit human vulnerabilities

[Back to index](#solutions-index)

**Phishing** is a social engineering attack in which the attacker pretends to be a trusted entity (a bank, employer, delivery company) to trick a victim into revealing sensitive information (passwords, OTPs, card numbers) or installing malware. It targets the **human**, not the software.

**How human vulnerabilities are exploited**

| Human weakness | How the attacker uses it | Example |
|----------------|--------------------------|---------|
| Trust in authority | Impersonates a bank, boss or government | "Message from your CEO: urgent transfer" |
| Urgency and fear | Threatens loss or penalty to prevent thinking | "Your account will be blocked in 24 hours" |
| Greed and curiosity | Offers a prize or interesting content | "You won a gift voucher, click to claim" |
| Helpfulness | Asks for a small favour | "Please review this attached invoice" |
| Lack of awareness, habit and distraction | Victim does not check the URL or sender | Fake login page with look-alike domain such as paypa1.com |

**Typical attack steps**

1. **Reconnaissance:** attacker collects information about the target (for spear phishing).
2. **Bait:** creates a convincing email, SMS or call with a spoofed sender and logo.
3. **Delivery:** sends it with a malicious link or attachment.
4. **Hook:** the victim clicks, lands on a **fake site**, and enters credentials, or opens an attachment that installs malware.
5. **Exploit:** the attacker logs in with the stolen credentials and steals data or money, or moves further into the organisation.

**Types:** email phishing, spear phishing (targeted), whaling (executives), smishing (SMS), vishing (voice call), and pharming (DNS redirection).

**Prevention:** check the sender and URL before clicking, never share OTPs or passwords, use **multi-factor authentication**, use email filters and browser warnings, keep software updated, and run awareness training and phishing simulations.

---

[Back to Solutions Index](#solutions-index) | [Back to top of README](#computer-networks-pt2-question-bank-2026)
