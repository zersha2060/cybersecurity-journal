<h1>DNS Traffic Analysis</h1>

<h2>1. Challenge Information</h2>

| Field |	Details |
| --- | --- |
| Platform	| CENTRI BTJA |
| Category	| Network Traffic Analysis |
| Challenge	| DNS Traffic Investigation |
| File Analyzed	| dns-traffic.pcap |
| Tools	| Wireshark, tcpdump |
| Protocol	| DNS |
| Status	| Completed |
| Date Completed	| [Date] | 

<h2>2. Challenge Overview</h2>

This challenge involves analyzing a provided PCAP file to investigate DNS traffic.

The objective is to inspect captured network packets, identify DNS queries and responses, and extract relevant information from the traffic.

<h2>3. Investigation Objectives</h2>

The investigation aims to identify:

1. The queried domain name.
2. The DNS response IP address.
3. The DNS record type.

<h2>4. Tools Used</h2>

| Tool |	Purpose |
| --- | --- |
| Wireshark	| Graphical packet inspection and protocol analysis |
| tcpdump	| Command-line PCAP inspection |

<h2>5. Investigation Methodology</h2>

<h3>5.1 Initial PCAP Inspection</h3>

I opened the provided PCAP file in Wireshark to inspect the captured network traffic.

The initial examination focused on identifying the protocols present in the capture and determining whether DNS traffic was included.

<h3>5.2 DNS Traffic Filtering</h3>

I applied the following Wireshark display filter:

```
dns
```

This narrowed the packet list to DNS-related traffic.

<h3>5.3 DNS Query Examination</h3>

I inspected the DNS query packets and examined the relevant packet fields.

The investigation focused on:

- DNS query name.
- Query type.
- Source and destination addresses.
- DNS transaction information.

<h3>5.4 DNS Response Examination</h3>

I examined the corresponding DNS response to identify the returned information.

The response was inspected for:

- Response code.
- Answer records.
- Returned IP address.
- DNS record type.

<h3>5.5 Command-Line Verification</h3>

I also used tcpdump to inspect DNS-related traffic in the provided PCAP.

Example command:

```
tcpdump -nn -r dns-traffic.pcap port 53
```

This provided an additional way to examine DNS traffic through the command line.

<h2>6. Findings</h2>

The following values are illustrative placeholders, not findings from an actual capture.

<h3>Finding 1 – Queried Domain</h3>

Question: What domain name was requested?
Observation: A DNS query for example.com was identified.
Evidence: DNS query packet.
Answer: example.com

<h3>Finding 2 – Resolved IP Address</h3>

Question: What IP address was returned?
Observation: The DNS response contained an illustrative A record.
Evidence: Corresponding DNS response packet.
Answer: 93.184.216.34

<h3>Finding 3 – DNS Record Type</h3>

Question: What DNS record type was used?
Observation: The query requested an IPv4 address.
Evidence: DNS query details.
Answer: A record.

<h2>7. Technical Analysis</h2>

DNS (Domain Name System) is responsible for translating domain names into corresponding network information.

In this investigation, the DNS query and response packets provided information about the requested domain and the returned DNS record.

Wireshark allowed the DNS protocol fields to be examined through its graphical interface, while tcpdump provided a command-line method for reviewing the same capture.

<h2>8. Conclusion</h2>

The investigation demonstrated how DNS traffic can be identified and analyzed through PCAP inspection.

By examining the DNS query and its corresponding response, relevant information about the requested domain and returned record could be extracted.

<h2>9. Lessons Learned</h2>

- Learned how DNS queries and responses appear in packet captures.
- Practiced filtering DNS traffic using Wireshark.
- Used tcpdump to inspect DNS traffic from a PCAP file.
- Understood the difference between DNS queries and responses.
- Learned how DNS record types provide different types of information.

<h2>10. Evidence</h2>

| Screenshot	| Description |
| --- | --- |
| 01-packet-overview.png | Initial PCAP inspection |
| 02-dns-filter.png	| DNS display filter |
| 03-packet-details.png	| DNS query and response fields |

<img width="852" height="852" alt="image" src="https://github.com/user-attachments/assets/8825398f-1203-4648-b63f-ebce334c2e5e" />


<h2>11. References</h2>

- Wireshark Documentation
- tcpdump Manual
- RFC 1035 – Domain Names

------------------------
Documented as part of my hands-on network traffic analysis and cybersecurity learning activities.
