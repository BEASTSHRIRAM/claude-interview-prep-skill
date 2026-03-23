# CN Reference -- Computer Networks

## OSI Model (7 Layers)

| Layer | Name | Role | Key Protocols |
|---|---|---|---|
| 7 | Application | User-facing services | HTTP, FTP, DNS, SMTP, SSH |
| 6 | Presentation | Data formatting, encryption | SSL/TLS, JPEG, ASCII |
| 5 | Session | Session management | NetBIOS, PPTP |
| 4 | Transport | End-to-end delivery, reliability | TCP, UDP |
| 3 | Network | Logical addressing, routing | IP, ICMP, OSPF, BGP |
| 2 | Data Link | Node-to-node delivery, MAC addressing | Ethernet, Wi-Fi, ARP |
| 1 | Physical | Bit transmission over medium | Cables, Hubs, Repeaters |

**TCP/IP Model (4 Layers)**
Application (covers OSI 5,6,7) | Transport | Internet (Network) | Network Access (Data Link + Physical)

---

## TCP vs UDP

| Feature | TCP | UDP |
|---|---|---|
| Connection | Connection-oriented (3-way handshake) | Connectionless |
| Reliability | Guaranteed delivery, retransmission | No guarantee |
| Ordering | Maintains order | No order guarantee |
| Speed | Slower (overhead) | Faster |
| Use cases | HTTP, FTP, email, SSH | DNS, video streaming, VoIP, gaming |
| Header size | 20 bytes minimum | 8 bytes |

**TCP 3-Way Handshake**
1. Client sends SYN (synchronize)
2. Server responds with SYN-ACK
3. Client sends ACK
Connection is established.

**TCP 4-Way Termination**
FIN, ACK, FIN, ACK

---

## IP Addressing

**IPv4**: 32-bit address, written as 4 octets. Example: 192.168.1.1
**IPv6**: 128-bit address, written as 8 groups of 4 hex digits.

**Private IP Ranges (not routable on public internet)**
- 10.0.0.0 to 10.255.255.255
- 172.16.0.0 to 172.31.255.255
- 192.168.0.0 to 192.168.255.255

**Subnetting**
CIDR notation: 192.168.1.0/24 means first 24 bits are network, last 8 are host.
Subnet mask /24 = 255.255.255.0, allows 254 hosts.

**NAT (Network Address Translation)**
Maps private IPs to a public IP. Allows multiple devices to share one public IP.

---

## DNS (Domain Name System)

Translates human-readable domain names (google.com) to IP addresses.

**Resolution Process**
1. Browser checks local cache
2. Checks OS hosts file
3. Queries Recursive Resolver (your ISP)
4. Resolver queries Root Name Server
5. Root refers to TLD Name Server (.com)
6. TLD refers to Authoritative Name Server
7. Authoritative returns IP
8. Resolver caches and returns to client

**Record Types**
- A: maps domain to IPv4
- AAAA: maps domain to IPv6
- CNAME: alias for another domain
- MX: mail server for domain
- NS: authoritative name server
- PTR: reverse DNS lookup

---

## HTTP and HTTPS

**HTTP Methods**: GET (retrieve), POST (create), PUT (replace), PATCH (partial update), DELETE (remove)

**HTTP Status Codes**
- 2xx: Success (200 OK, 201 Created, 204 No Content)
- 3xx: Redirection (301 Moved Permanently, 302 Found)
- 4xx: Client Error (400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found)
- 5xx: Server Error (500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable)

**HTTP vs HTTPS**
HTTPS uses TLS (Transport Layer Security) to encrypt traffic. TLS handshake establishes encryption keys before data transfer.

**HTTP/1.1 vs HTTP/2 vs HTTP/3**
- HTTP/1.1: one request per connection (keep-alive allows reuse but still sequential)
- HTTP/2: multiplexing (multiple requests over one connection), header compression
- HTTP/3: uses QUIC (UDP-based), eliminates head-of-line blocking, faster connection setup

---

## Routing Protocols

**RIP (Routing Information Protocol)**
Distance vector protocol. Uses hop count as metric (max 15 hops). Slow convergence. Bellman-Ford algorithm.

**OSPF (Open Shortest Path First)**
Link state protocol. Uses Dijkstra's algorithm. Fast convergence. Maintains full topology map.

**BGP (Border Gateway Protocol)**
Path vector protocol. Used between Autonomous Systems on the internet (inter-domain routing). The backbone of internet routing.

---

## Congestion Control (TCP)

**Slow Start**: begins with a small congestion window (cwnd), doubles each RTT until threshold.
**Congestion Avoidance**: after threshold, increase cwnd by 1 MSS per RTT (linear growth).
**Fast Retransmit**: if 3 duplicate ACKs received, retransmit lost segment without waiting for timeout.
**Fast Recovery**: after fast retransmit, reduce threshold and cwnd, then enter congestion avoidance (not slow start).

---

## Important Protocols and Their Ports

| Protocol | Port |
|---|---|
| HTTP | 80 |
| HTTPS | 443 |
| FTP | 21 |
| SSH | 22 |
| SMTP | 25 |
| DNS | 53 |
| DHCP | 67/68 |
| POP3 | 110 |
| IMAP | 143 |

---

## Common Interview Questions

1. What happens when you type a URL in a browser?
2. What is the difference between TCP and UDP? When would you use each?
3. Explain the 3-way handshake.
4. What is ARP and why is it needed?
5. What is the difference between a hub, switch, and router?
6. What is DHCP and how does it work?
7. What is a firewall? Types of firewalls?
8. What is the difference between HTTP and HTTPS?
9. What is a proxy server and a reverse proxy?
10. What is the difference between symmetric and asymmetric encryption in TLS?
11. What is a VPN and how does it work?
12. What is ICMP? What is ping?
13. Explain how a CDN works.
14. What is the difference between latency, bandwidth, and throughput?
15. What is socket programming? What is a socket?
