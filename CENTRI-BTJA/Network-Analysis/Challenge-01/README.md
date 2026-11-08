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

I used Wireshark display filters to narrow down specific types of network traffic and identify packets relevant to the challenge questions.

Examples of relevant display filters include:

```
tcp
udp
icmp
dns
tcp.port == 3942 || udp.port == 3942
tcp.port == 8081
```

These filters helped isolate specific protocols, communication ports, and network activity for further examination.

<h3>5.4 Conversations Analysis</h3>

I examined the Conversations statistics in Wireshark to identify communication between network hosts.

I focused on conversations with significant packet counts and traffic volume to identify potentially suspicious communication patterns.

The source and destination IP addresses from these conversations provided useful information for identifying hosts that required further investigation.

<h3>5.5 Endpoint Analysis</h3>

I used Wireshark's Endpoints statistics to examine the hosts involved in the captured network traffic.

I compared the traffic statistics to identify the top talkers, particularly hosts responsible for transmitting significant amounts of data.

This helped narrow down potentially suspicious IP addresses that could be investigated further.

<h3>5.6 Suspicious Host Investigation</h3>

After identifying potentially suspicious IP addresses, I examined their communication patterns and the protocols associated with their network activity.

I correlated the suspicious hosts with the information gathered from the Protocol Hierarchy, Conversations, and Endpoints statistics.

This helped identify relevant network connections and narrow down the traffic associated with the challenge.

<h3>5.7 Port Identification and Stream Analysis</h3>

I examined the communication involving the identified suspicious hosts to determine which ports were used during the captured network activity.

After identifying relevant ports, I filtered the traffic to isolate the corresponding communication sessions.

I then used Wireshark's Follow Stream feature to reconstruct and inspect the application-level communication.

This allowed me to examine the exchanged data and identify relevant information, including authentication details, server information, and file-related activity.

<h2>6. Findings</h2>

The following findings were obtained from analyzing the two provided PCAPNG files.

<h3>6.1 PCAP1 – Protocol Identification</h3>

**Question:** Which protocol was used over port 3942?

**Observation:** I examined the traffic associated with port 3942 and identified the protocol used for communication.

**Analysis:** I inspected the packet details and protocol information associated with the specified port.

**Answer:** SSDP

<h3>6.2 PCAP1 – ICMP Traffic Analysis</h3>

**Question:** What is the IP address of the host that was pinged twice?

**Observation:** I examined the ICMP traffic to identify Echo Request packets and their destination addresses.

**Analysis:** I inspected the ICMP packets and identified the destination host that received two ping requests.

**Answer:** 8.8.4.4

<h3>6.3 PCAP1 – DNS Traffic Analysis</h3>

**Question:** How many DNS query response packets were captured?

**Observation:** I filtered the captured traffic to display DNS response packets.

**Analysis:** I examined the filtered packet list and counted the DNS responses captured in the file.

**Answer:** 90

<h3>6.4 PCAP1 – Network Traffic Statistics</h3>

**Question:** What is the IP address of the host which sent the most number of bytes?

**Observation:** I examined the Endpoints statistics to identify the host responsible for transmitting the highest amount of network traffic.

**Analysis:** I compared the transmitted byte counts associated with the different IP addresses.

**Answer:** 115.178.9.18

<h3>6.5 PCAP2 – WebAdmin Credential Identification</h3>

**Question:** What is the WebAdmin password?

**Observation:** I investigated the captured application traffic to identify authentication-related information associated with WebAdmin.

**Analysis:** I examined the relevant communication and packet contents to locate the WebAdmin credentials.

**Answer:** sbt123

<h3>6.6 PCAP2 – FTP Server Identification</h3>

**Question:** What is the version number of the attacker's FTP server?

**Observation:** I examined the FTP traffic to identify information about the attacker's FTP server.

**Analysis:** I inspected the FTP server identification information exchanged during the communication.

**Answer:** 1.5.5

<h3>6.7 PCAP2 – Access Port Identification</h3>

**Question:** Which port was used to gain access to the victim Windows host?

**Observation:** I examined the network conversations involving the suspicious host and the victim Windows machine.

**Analysis:** I identified the relevant communication port associated with access to the victim host.

**Answer:** 8081

<h3>6.8 PCAP2 – Confidential File Identification</h3>

**Question:** What is the name of a confidential file that is on the Windows host?

**Observation:** I examined the application-level communication and file-related information associated with the victim Windows host.

**Analysis:** I inspected the relevant captured data to identify the name of a confidential document.

**Answer:** Employee_Information_CONFIDENTIAL.txt

<h3>6.9 PCAP2 – Log File Identification</h3>

**Question:** What is the name of the log file that was created at 4:51 AM on the Windows host?

**Observation:** I investigated the captured traffic for file-related activity associated with the victim Windows host.

**Analysis:** I examined the available file information and associated timestamps to identify the log file created at the specified time.

**Answer:** LogFile.log

<h2>7. Technical Analysis</h2>

The investigation demonstrated how different Wireshark features can be used to identify and examine network activity within packet captures.

The Protocol Hierarchy provided an overview of the protocols present in the captures, while Conversations and Endpoints helped identify communication patterns and hosts generating significant network traffic.

By examining suspicious IP addresses and their associated communication ports, I was able to narrow down relevant network sessions for further investigation.

The Follow Stream feature provided a way to reconstruct application-level communication and inspect information exchanged between network hosts.

These techniques helped identify relevant network details, including protocol information, host addresses, authentication data, server versions, and file-related information.

<h2>8. Conclusion</h2>

The challenge provided practical experience in analyzing network traffic using Wireshark and investigating two different PCAPNG files.

By examining protocol distributions, network conversations, and endpoint statistics, I practiced identifying potentially suspicious hosts and investigating their communication patterns.

I also gained experience filtering network traffic, identifying relevant ports, and examining application-level communication through Follow Stream.

Overall, this challenge strengthened my understanding of packet analysis and demonstrated how network traffic inspection can help uncover useful information during a network investigation.

<h2>9. Lessons Learned</h2>

- Learned how to analyze PCAPNG files using Wireshark.
- Practiced identifying protocols through Protocol Hierarchy.
- Used Conversations to examine communication between network hosts.
- Used Endpoints to identify hosts generating significant network traffic.
- Learned how to identify potentially suspicious IP addresses through traffic statistics.
- Practiced filtering traffic based on protocols, IP addresses, and ports.
- Used Follow Stream to examine application-level communication.
- Learned how packet captures can reveal authentication information, server details, and file-related activity.
- Improved my understanding of network traffic analysis and basic network forensics.

<h2>10. Evidence</h2>

| Screenshot | Description |
| --- | --- |
| 01-pcap1-overview.png | Initial inspection of SBT-PCAP1.pcapng |
| 02-protocol-hierarchy.png | Protocol distribution in the packet capture |
| 03-conversations.png | Communication statistics between network hosts |
| 04-endpoints.png | Endpoint statistics and traffic volume |
| 05-icmp-analysis.png | ICMP traffic showing ping requests |
| 06-dns-analysis.png | DNS response packet analysis |
| 07-pcap2-overview.png | Initial inspection of SBT-PCAP2.pcapng |
| 08-ftp-analysis.png | FTP server information |
| 09-stream-analysis.png | Reconstructed application-level communication |
| 10-file-analysis.png | File-related information identified in the capture |

<h2>11. References</h2>

- Wireshark Documentation
- Wireshark Display Filter Reference
- Wireshark User's Guide
- PCAPNG File Format Specification

---

Documented as part of my hands-on network traffic analysis and cybersecurity learning activities.
