# Network Foundations

### Open Systems Interconnection (OSI)

| Layer | Name         | Addressing                 |
| ----- | ------------ | -------------------------- |
| 1     | Physical     |                            |
| 2     | Data Link    | Media Access Control (MAC) |
| 3     | Network      | Internet Protocol (IP)     |
| 4     | Transport    | Port number                |
| 5     | Session      |                            |
| 6     | Presentation |                            |
| 7     | Application  |                            |

### TCP/IP

| Layer | Name        |
| ----- | ----------- |
| 1     | Link        |
| 2     | Internet    |
| 3     | Transport   |
| 4     | Application |

### Transmission Modes

- **Simplex mode** allows one-way communication only (keyboard to computer)
- **Half-duplex mode** allows alternating two-directional communication
- **Full-duplex mode** allows two-way communication simultaneously

### Dynamic Host Configuration Protocol (DHCP)

| Step        | Source | Destination |
| ----------- | ------ | ----------- |
| Discover    | Client | Server      |
| Offer       | Server | Client      |
| Request     | Client | Server      |
| Acknowledge | Server | Client      |

### Network Address Translation (NAT)

- Public IP addresses are assigned by ISPs and can be accessed from anywhere on the internet
- Private IP addresses are non-routable and assigned to hosts within a LAN
- Most common form at home is Port Address Translation (PAT) where each connection gets its own port
- There is also "static NAT" (1:1 public IP address to private IP address) and "dynamic NAT" (a pool of shared public IP addresses)

### Domain Name System (DNS)

1. Search local DNS cache
2. Query **recursive DNS server** (ISP or i.e. `8.8.8.8`)
3. Recursive DNS server contacts **root DNS server** which returns the IP address of the Top Level Domain (TLD) name server
4. Recursive DNS server contact TLD name server which directs the query to the **authoritative name server** for the second-level domain (`example.com`)
5. Authoritative name server returns IP address for `example.com` to recursive DNS server
6. Recursive DNS server responds to the requesting host device with the resolved IP address for `example.com`.
