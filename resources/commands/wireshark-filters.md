
# Wireshark Display Filter Reference

A collection of Wireshark display filters used during network traffic analysis, packet inspection, and cybersecurity investigations.

---

## 1. Protocol Filters

Protocol filters allow you to isolate packets belonging to specific network protocols.

| Display Filter | Description |
|---|---|
| `dns` | Displays DNS traffic |
| `http` | Displays HTTP traffic |
| `https` | Not a standard Wireshark display filter; use `tls` for TLS traffic |
| `tcp` | Displays TCP traffic |
| `udp` | Displays UDP traffic |
| `icmp` | Displays ICMP traffic |
| `tls` | Displays TLS traffic |
| `arp` | Displays ARP traffic |
| `ftp` | Displays FTP traffic |
| `ssh` | Displays SSH traffic |
| `dhcp` | Displays DHCP traffic |

## 2. IP Address Filters

These filters help identify traffic associated with specific IP addresses.

| Display Filter | Description |
|---|---|
| `ip.addr == 192.168.1.10` | Displays traffic involving the specified IP |
| `ip.src == 192.168.1.10` | Displays packets originating from the specified IP |
| `ip.dst == 192.168.1.10` | Displays packets destined for the specified IP |
| `ip.addr == 192.168.1.0/24` | Displays traffic involving the specified subnet |

## 3. TCP Filters

TCP filters are useful when investigating connections, connection attempts, and TCP flags.

| Display Filter | Description |
|---|---|
| `tcp.port == 80` | Displays TCP traffic using port 80 |
| `tcp.port == 443` | Displays TCP traffic using port 443 |
| `tcp.srcport == 443` | Displays packets originating from TCP port 443 |
| `tcp.dstport == 80` | Displays packets destined for TCP port 80 |
| `tcp.flags.syn == 1` | Displays packets with the SYN flag set |
| `tcp.flags.ack == 1` | Displays packets with the ACK flag set |
| `tcp.flags.reset == 1` | Displays packets with the RST flag set |
| `tcp.flags.fin == 1` | Displays packets with the FIN flag set |

## 4. UDP Filters

Useful for investigating UDP-based communication and services.

| Display Filter | Description |
|---|---|
| `udp.port == 53` | Displays UDP traffic using port 53 |
| `udp.port == 67` | Displays UDP traffic using port 67 |
| `udp.port == 68` | Displays UDP traffic using port 68 |
| `udp.srcport == 53` | Displays packets originating from UDP port 53 |
| `udp.dstport == 53` | Displays packets destined for UDP port 53 |

## 5. DNS Filters

Useful for identifying DNS queries, responses, and specific DNS record types.

| Display Filter | Description |
|---|---|
| `dns` | Displays all DNS packets |
| `dns.flags.response == 0` | Displays DNS queries |
| `dns.flags.response == 1` | Displays DNS responses |
| `dns.qry.name == "example.com"` | Displays queries for a specific domain |
| `dns.qry.type == 1` | Displays queries for A records |
| `dns.qry.type == 28` | Displays queries for AAAA records |
| `dns.flags.rcode != 0` | Displays DNS responses with non-zero response codes |

## 6. HTTP Filters

Useful for inspecting unencrypted HTTP requests and responses.

| Display Filter | Description |
|---|---|
| `http` | Displays HTTP traffic |
| `http.request` | Displays HTTP requests |
| `http.response` | Displays HTTP responses |
| `http.request.method == "GET"` | Displays HTTP GET requests |
| `http.request.method == "POST"` | Displays HTTP POST requests |
| `http.host == "example.com"` | Displays HTTP traffic for a specific host |
| `http.response.code == 200` | Displays HTTP responses with status code 200 |

> **Note:** HTTPS traffic is encrypted. TLS traffic can be inspected at the protocol level, but application-layer HTTP contents generally require appropriate decryption.

## 7. Logical Operators

Wireshark supports logical operators that allow multiple filter conditions to be combined.

| Operator | Description | Example |
|---|---|---|
| `&&` | AND – both conditions must match | `tcp && ip.addr == 192.168.1.10` |
| `||` | OR – either condition may match | `dns || http` |
| `!` | NOT – excludes matching packets | `!arp` |

### Example Combined Filters

```text
dns && ip.addr == 192.168.1.10
```

Displays DNS packets involving a specific IP address.

```text
tcp.port == 443 && ip.src == 192.168.1.10
```

Displays TCP traffic involving source IP 192.168.1.10 and port 443.

```text
http || dns
```

Displays HTTP or DNS traffic.

## 8. Useful Wireshark Features

| Feature | Purpose |
|---|---|
| Statistics → Protocol Hierarchy | Shows protocols identified in the capture |
| Statistics → Conversations | Displays communication between endpoints |
| Statistics → Endpoints | Lists network endpoints |
| Follow → TCP Stream | Reconstructs a TCP conversation |
| Follow → UDP Stream | Examines a UDP conversation |
| Export Objects | Extracts supported objects from captured protocols |

## 9. Notes

- These are Wireshark **display filters**, not capture filters.
- Display filters are applied after packets have been captured or loaded.
- Field names and supported protocol filters may vary by Wireshark version.
- Always verify findings against the relevant packet details.
- Filter results should be interpreted in the context of the entire network investigation.

## 10. References

- [Wireshark Display Filter Reference](https://www.wireshark.org/docs/dfref/)
- [Wireshark User's Guide](https://www.wireshark.org/docs/wsug_html_chunked/)
- [Wireshark Documentation](https://www.wireshark.org/docs/)

---

*Personal technical reference for network traffic analysis and cybersecurity investigations.*
