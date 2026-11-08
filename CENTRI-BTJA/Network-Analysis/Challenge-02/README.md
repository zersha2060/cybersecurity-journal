
<h1>SBT tcpdump Challenge – Network Traffic Analysis</h1>

<h2>1. Challenge Information</h2>

| Field | Details |
| --- | --- |
| Platform | CENTRI BTJA |
| Category | Network Traffic Analysis |
| Challenge | Tcpdump Challenge |
| Files Analyzed | PCAP4, PCAP5 |
| Tools | tcpdump, Linux Command Line |
| Protocols | TCP, UDP, HTTP, SSH |
| Status | Completed |
| Date Completed | September 18, 2026 |

<h2>2. Challenge Overview</h2>

This challenge involves analyzing two provided PCAP files using tcpdump, a command-line packet analyzer.

The objective is to inspect captured network traffic, identify specific packet characteristics, examine protocol information, and extract relevant details based on the challenge requirements.

The investigation focuses on using tcpdump filters and Linux command-line utilities to analyze packet captures without relying on a graphical packet analysis interface.

<h2>3. Investigation Objectives</h2>

The investigation aims to identify:

1. The number of captured UDP packets.
2. The number of TCP packets with both SYN and ACK flags set.
3. The Chrome browser version used to connect to a specific website.
4. The number of packets with a TTL value of 38.
5. The name of a PNG file hosted on a web server.
6. The OpenSSH version running on a server.
7. The port used to serve a ZIP file.
8. The capture timestamp of a packet with a specific TCP checksum value.

<h2>4. Tools Used</h2>

| Tool | Purpose |
| --- | --- |
| tcpdump | Command-line packet capture inspection and filtering |
| grep | Search packet output for specific text and patterns |
| wc | Count lines returned by commands |
| less | Inspect packet output one screen at a time |
| Linux Command Line | Execute and combine packet analysis commands |

<h2>5. Investigation Methodology</h2>

<h3>5.1 Initial PCAP Inspection</h3>

I used tcpdump with the `-r` option to read the provided PCAP files and inspect their captured network traffic.

The investigation involved analyzing PCAP4 and PCAP5 separately to identify the information required by the challenge questions.

<h3>5.2 UDP Packet Counting</h3>

I used tcpdump to filter UDP traffic from PCAP4 and piped the output into the `wc -l` command to count the resulting lines.

Command:

```bash
tcpdump -r name_of_pcap udp | wc -l
```

The `-r` option reads packets from an existing capture file, while the `udp` filter displays UDP traffic.

The `wc -l` command counts the output lines to determine the number of matching packets.

<h3>5.3 TCP SYN and ACK Flag Analysis</h3>

I used a tcpdump filter to identify TCP packets with both the SYN and ACK flags set.

Command:

```bash
tcpdump -r name_of_pcap -n 'tcp[tcpflags] == 18' | wc -l
```

The TCP flags field is examined using a bitmask value of 18, which represents the combination of SYN (2) and ACK (16).

The `-n` option prevents hostname and port resolution, keeping the output in numerical format.

The matching packets were counted using `wc -l`.

<h3>5.4 HTTP User-Agent Inspection</h3>

I examined HTTP traffic on port 80 to identify the browser information contained in the HTTP User-Agent header.

Command:

```bash
tcpdump -r name_of_pcap -n -A 'tcp port 80' | grep -i 'User-Agent:'
```

The `-A` option displays packet contents in ASCII format, allowing readable HTTP headers to be inspected.

I used `grep -i` to search for the User-Agent header without considering letter case.

The User-Agent information provided details about the browser used to access the website.

<h3>5.5 TTL Value Analysis</h3>

I used a tcpdump filter to identify packets with a specific IP Time to Live (TTL) value.

Command:

```bash
tcpdump -r name_of_pcap -n 'ip[8] == 38' | wc -l
```

The expression `ip[8]` accesses the TTL field in the IPv4 header.

The filter selects packets with a TTL value of 38, while `wc -l` counts the matching packets.

<h3>5.6 PNG File Identification</h3>

For PCAP5, I examined traffic associated with the specified web server to identify references to PNG files.

Command:

```bash
tcpdump -r name_of_pcap -n -A 'host [ip addr]' | grep -i 'png'
```

The `host` filter restricts the traffic to packets involving the specified IP address.

The `-A` option displays packet contents in ASCII format, while `grep -i` searches for PNG-related references.

This helped identify the name of the PNG file associated with the web server.

<h3>5.7 SSH Server Version Identification</h3>

I inspected the traffic involving the specified server to identify its SSH version information.

Command:

```bash
tcpdump -r name_of_pcap -n -A 'host [ip addr]' | grep -i 'SSH-'
```

SSH servers commonly identify themselves through a version string exchanged during connection establishment.

I searched the captured traffic for the SSH identification string to determine the server software and version.

<h3>5.8 ZIP File Port Identification</h3>

I examined the traffic associated with the web server to identify the port used to serve the ZIP file.

I inspected the server-related packet contents and communication details to identify the relevant service port.

<h3>5.9 TCP Checksum Analysis</h3>

I used tcpdump to filter packets based on a specific TCP checksum value.

Command:

```bash
tcpdump -r name_of_pcap -n 'tcp[16:2] == 53203'
```

The expression `tcp[16:2]` accesses the two-byte TCP checksum field in the TCP header.

The filter identifies packets with a TCP checksum value of 53203.

I then examined the timestamp displayed in the tcpdump output to determine when the matching packet was captured.

<h2>6. Findings</h2>

The following findings were obtained from analyzing PCAP4 and PCAP5 using tcpdump.

<h3>6.1 PCAP4 – UDP Packet Count</h3>

**Question:** How many UDP packets have been captured?

**Observation:** I filtered the packet capture to display UDP traffic and counted the matching output lines.

**Analysis:** I used the UDP filter together with the `wc -l` command to determine the number of captured UDP packets.

**Answer:** 3290

<h3>6.2 PCAP4 – TCP SYN and ACK Flags</h3>

**Question:** How many TCP packets have both the SYN and ACK flags set?

**Observation:** I filtered the TCP traffic to identify packets with the SYN and ACK flags set.

**Analysis:** I used the TCP flags field and a bitmask value of 18 to identify matching packets, then counted the results.

**Answer:** 20

<h3>6.3 PCAP4 – Chrome Version Identification</h3>

**Question:** Which version of Chrome was used to connect to securityblue.team?

**Observation:** I inspected HTTP traffic on port 80 and searched for the User-Agent header.

**Analysis:** The User-Agent information identified the browser and its version used in the HTTP communication with the website.

**Answer:** 80.0.3987.87

<h3>6.4 PCAP4 – TTL Value Analysis</h3>

**Question:** How many packets have a TTL value of 38?

**Observation:** I filtered the captured IPv4 packets based on their TTL field.

**Analysis:** I used the `ip[8] == 38` filter to identify packets with the specified TTL value and counted the results.

**Answer:** 710

<h3>6.5 PCAP5 – PNG File Identification</h3>

**Question:** What is the name of the PNG file on the web server at 192.168.56.111?

**Observation:** I inspected the traffic involving the specified web server and searched the packet contents for PNG-related references.

**Analysis:** I used the host filter together with ASCII packet output and grep to identify the PNG filename.

**Answer:** proprietary.png

<h3>6.6 PCAP5 – OpenSSH Version Identification</h3>

**Question:** Which version of OpenSSH is running on the server?

**Observation:** I examined the traffic involving the server and searched for SSH identification strings.

**Analysis:** I inspected the SSH version information exchanged during the connection establishment.

**Answer:** 7.9p1

<h3>6.7 PCAP5 – ZIP File Port Identification</h3>

**Question:** On which port is the ZIP file being served?

**Observation:** I examined the web server communication and investigated the traffic associated with the ZIP file.

**Analysis:** I identified the port used by the server to provide the ZIP file.

**Answer:** 3016

<h3>6.8 PCAP5 – TCP Checksum Timestamp</h3>

**Question:** When was a packet with a TCP checksum value of 53203 captured?

**Observation:** I filtered the packet capture using the specified TCP checksum value.

**Analysis:** I examined the timestamp of the matching packet in the tcpdump output.

**Answer:** 06:04:46.207925

<h2>7. Technical Analysis</h2>

This challenge demonstrated how tcpdump can be used to investigate network traffic directly from the command line.

Unlike graphical packet analyzers, tcpdump allows packet captures to be filtered and examined using command-line expressions. Its output can also be combined with Linux utilities such as grep and wc to search for specific information and count matching packets.

During the investigation, I used protocol filters to identify UDP and TCP traffic, examined TCP flags, inspected HTTP User-Agent headers, and accessed IPv4 and TCP header fields to identify specific packet characteristics.

I also examined application-level information within the captured traffic to identify browser versions, SSH server details, filenames, and service ports.

The challenge reinforced the usefulness of tcpdump for packet inspection, traffic filtering, and network troubleshooting.

<h2>8. Conclusion</h2>

The challenge provided practical experience in analyzing packet captures using tcpdump and Linux command-line utilities.

By examining PCAP4 and PCAP5, I practiced filtering network traffic, counting packets, inspecting TCP flags, identifying TTL values, and extracting information from captured application traffic.

I also gained experience using tcpdump expressions to inspect specific fields within IP and TCP headers.

Overall, this challenge strengthened my understanding of command-line network traffic analysis and demonstrated how packet-level information can be extracted without relying on a graphical interface.

<h2>9. Lessons Learned</h2>

- Learned how to read existing PCAP files using tcpdump.
- Practiced filtering UDP and TCP traffic.
- Understood how TCP SYN and ACK flags can be identified using bitmask expressions.
- Learned how to inspect HTTP User-Agent headers to identify browser information.
- Practiced examining the TTL field in IPv4 packets.
- Learned how to search packet contents using grep.
- Used wc to count matching packet output.
- Learned how SSH identification strings reveal server software information.
- Practiced filtering packets using specific TCP header fields.
- Improved my understanding of command-line packet analysis and network forensics.

<h2>10. Evidence</h2>

| Screenshot | Description |
| --- | --- |
| 01-udp-count.png | UDP packet count from PCAP4 |
| 02-tcp-flags.png | TCP SYN and ACK packet count |
| 03-user-agent.png | HTTP User-Agent information showing Chrome version |
| 04-ttl-analysis.png | Packets with a TTL value of 38 |
| 05-png-identification.png | PNG filename identified from PCAP5 |
| 06-ssh-version.png | SSH server identification string |
| 07-zip-port.png | Port used to serve the ZIP file |
| 08-tcp-checksum.png | Matching TCP checksum and packet timestamp |

<h2>11. References</h2>

- tcpdump Manual
- tcpdump and libpcap Documentation
- Wireshark Documentation
- Linux Manual Pages

---

Documented as part of my hands-on network traffic analysis and cybersecurity learning activities.
