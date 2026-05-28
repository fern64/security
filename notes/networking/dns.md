# Domain Name System (DNS)

1. Search local DNS cache
2. Query **recursive DNS server** (ISP or i.e. `8.8.8.8`)
3. Recursive DNS server contacts **root DNS server** which returns the IP address of the Top Level Domain (TLD) name server
4. Recursive DNS server contact TLD name server which directs the query to the **authoritative name server** for the second-level domain (`example.com`)
5. Authoritative name server returns IP address for `example.com` to recursive DNS server
6. Recursive DNS server responds to the requesting host device with the resolved IP address for `example.com`.
