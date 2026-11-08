<h1>SBT Wireshark Challenge – Network Traffic Analysis</h1>

<h2>1. Challenge Information</h2>

| Field | Details |
| --- | --- |
| Platform | SBT |
| Category | Network Traffic Analysis |
| Challenge | Wireshark Challenge |
| Files Analyzed | SBT-PCAP1.pcapng, SBT-PCAP2.pcapng |
| Tools | Wireshark |
| Protocols | Multiple (depending on captured traffic) |
| Status | Completed |
| Date Completed | Sept. 13, 2026 |

<h2>2. Challenge Overview</h2>

This challenge involves analyzing two provided PCAP files to investigate captured network traffic and identify relevant information based on the challenge requirements.

The objective is to examine network packets, identify communication patterns, inspect protocol-specific information, and extract relevant details from the captured traffic.

Both PCAP files are analyzed to identify important network events and answer the questions associated with the challenge.

<h2>3. Investigation Objectives</h2>

The investigation aims to:

1. Examine the contents of both PCAP files.
2. Identify the protocols and network services involved.
3. Analyze relevant packets and communication sessions.
4. Identify important source and destination addresses.
5. Extract relevant information from packet contents.
6. Correlate findings between the two PCAP files where applicable.
7. Answer the questions provided in the challenge.

<h2>4. Tools Used</h2>

| Tool | Purpose |
| --- | --- |
| Wireshark | Graphical packet inspection and protocol analysis |
| Display Filters | Narrow down traffic based on specific protocols and packet attributes |
| Follow Stream | Reconstruct application-level communication |

<h2>5. Investigation Methodology</h2>

<h3>5.1 Initial PCAP Inspection</h3>

I opened the first PCAP file in Wireshark to examine the captured network traffic.

I repeated the same process for the second PCAP file to identify the protocols, communication patterns, and relevant network activity.

The initial examination focused on:

- Total number of captured packets.
- Protocol distribution.
- Source and destination IP addresses.
- Communication between hosts.
- Potentially interesting network activity.

<h3>5.2 Protocol Identification</h3>

I examined the Protocol Hierarchy in Wireshark to identify the protocols present in each capture.

This helped determine which types of network traffic were involved and which protocols required further investigation.

<h3>5.3 Packet Filtering and Analysis</h3>

I applied appropriate Wireshark display filters to narrow down the captured traffic.

Examples of filters used during the investigation:
