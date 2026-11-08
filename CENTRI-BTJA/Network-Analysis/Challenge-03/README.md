
<h1>Network Analysis Challenge – MitM Attack Investigation</h1>

<h2>1. Challenge Information</h2>

| Field | Details |
| --- | --- |
| Platform | CENTRI BTJA |
| Category | Network Traffic Analysis |
| Challenge | Network Analysis |
| File Analyzed | PCAP3 |
| Tools | Wireshark, tcpdump |
| Protocols | ARP, SSH, TCP |
| Attack Type | Man-in-the-Middle (MitM) |
| Status | Completed |
| Date Completed | September 20, 2026 |

<h2>2. Challenge Overview</h2>

This challenge involves investigating a simulated network intrusion within the internal network of a fictional cybersecurity company called Alexis.

According to the scenario, an attacker gained unauthorized physical access to the company's premises by connecting a laptop to an unused switch port. This provided the attacker with access to the internal network.

The attacker then attempted to intercept communications between the central server and another host to obtain SSH credentials that could potentially be used to access the central server.

The objective is to analyze the provided PCAP file, identify the attacker's device, determine the type of attack taking place, and extract relevant information from the captured network traffic.

<h2>3. Investigation Objectives</h2>

The investigation aims to identify:

1. The MAC address of the attacker.
2. The type of attack used to intercept network communications.
3. The file downloaded from the central server.
4. The department associated with a specific employee.
5. The SSH password of the Domain Administrator.

<h2>4. Tools Used</h2>

| Tool | Purpose |
| --- | --- |
| Wireshark | Graphical packet inspection and network traffic analysis |
| tcpdump | Command-line packet capture inspection |
| Display Filters | Isolate relevant network protocols and packets |
| Follow Stream | Reconstruct and inspect application-level communication |

<h2>5. Investigation Methodology</h2>

<h3>5.1 Initial PCAP Inspection</h3>

I opened the provided PCAP file in Wireshark to examine the captured network traffic.

The initial inspection focused on understanding the network communication between the hosts, identifying the protocols present, and examining the traffic associated with the central server.

I also considered the attack scenario to determine which network activities required further investigation.

<h3>5.2 MAC Address Identification</h3>

I examined the captured network traffic to identify the devices communicating within the internal network.

The investigation focused on examining Ethernet source and destination addresses and identifying the MAC address associated with the attacker's device.

The identified MAC address was used to distinguish the attacker's device from the other network hosts.

<h3>5.3 ARP Traffic Analysis</h3>

I examined ARP (Address Resolution Protocol) traffic to investigate how devices were identifying one another within the local network.

ARP is responsible for mapping IP addresses to MAC addresses within a local network.

Since the scenario involved an attacker intercepting communications between two hosts, ARP activity was relevant to investigating possible address manipulation and traffic redirection.

I examined the ARP information to understand how network addresses were being associated with physical devices.

<h3>5.4 Man-in-the-Middle Attack Identification</h3>

Based on the scenario and captured network traffic, I investigated the possibility of a Man-in-the-Middle (MitM) attack.

A MitM attack occurs when an attacker positions themselves between two communicating devices, allowing them to intercept or potentially manipulate the exchanged traffic.

I examined the relevant network communication and ARP activity to identify indications of traffic interception between the central server and another host.

<h3>5.5 File Transfer Investigation</h3>

I examined the captured communication to identify files transferred from the central server.

The investigation focused on application-level traffic and file-related information available within the packet capture.

I inspected the relevant communication to identify the filename associated with the downloaded data.

<h3>5.6 Employee Information Identification</h3>

After identifying the downloaded file, I examined its available contents to locate the employee information requested by the challenge.

The investigation focused on finding the employee's name and determining the department associated with that individual.

<h3>5.7 SSH Credential Investigation</h3>

I examined the captured SSH-related communication to investigate the exposure of authentication information.

The investigation focused on identifying relevant credentials associated with the Domain Administrator.

I examined the available packet contents and communication details to determine the password requested by the challenge.

<h2>6. Findings</h2>

The following findings were obtained from analyzing the provided PCAP file.

<h3>6.1 Attacker MAC Address Identification</h3>

**Question:** What is the MAC address of the attacker?

**Observation:** I examined the Ethernet addresses in the captured network traffic to identify the device associated with the suspicious network activity.

**Analysis:** I inspected the source and destination MAC addresses associated with the relevant communication to identify the attacker's device.

**Answer:** 08:00:27:3d:27:5d

<h3>6.2 Attack Type Identification</h3>

**Question:** What is the type of attack which is taking place that allows the attacker to listen in on conversations between the central server and another host?

**Observation:** The scenario describes an attacker intercepting communications between two devices within the company's internal network.

**Analysis:** I examined the network activity and ARP-related information to investigate the interception of communications between the central server and another host.

**Answer:** Man-in-the-Middle (MitM) Attack

<h3>6.3 File Download Identification</h3>

**Question:** What is the file which was downloaded from the central server?

**Observation:** I investigated the captured communication to identify file-related information associated with the central server.

**Analysis:** I examined the relevant application-level data and identified the filename associated with the transferred file.

**Answer:** Alevis_Employee_Information_Chart.csv

<h3>6.4 Employee Department Identification</h3>

**Question:** What department does Borden Danilevich work at?

**Observation:** I examined the employee information contained in the downloaded CSV file.

**Analysis:** I located the employee's name in the available information and identified the department associated with the employee.

**Answer:** Sales

<h3>6.5 Domain Administrator SSH Password Identification</h3>

**Question:** What is the SSH password of the Domain Administrator?

**Observation:** I investigated the captured network communication to identify authentication information associated with the Domain Administrator.

**Analysis:** I examined the relevant captured data and identified the password requested by the challenge.

**Answer:** gMR<4eXf]e6W

<h2>7. Technical Analysis</h2>

This challenge demonstrated how network traffic analysis can be used to investigate a Man-in-the-Middle attack and identify information exposed through intercepted communications.

A Man-in-the-Middle attack occurs when an attacker positions themselves between two communicating hosts, potentially allowing them to observe or manipulate network traffic.

ARP (Address Resolution Protocol) is particularly relevant to this type of attack because it is used to associate IP addresses with MAC addresses within a local network.

By examining Ethernet addresses and ARP-related traffic, it is possible to investigate suspicious address mappings and identify devices potentially involved in traffic interception.

The investigation also demonstrated how information transmitted across a network can expose sensitive data, including transferred files, employee information, and authentication credentials.

This highlights the importance of secure communication protocols, proper network segmentation, and monitoring for suspicious network activity.

<h2>8. Conclusion</h2>

The challenge provided practical experience in investigating network traffic associated with a simulated internal network intrusion.

By examining the provided PCAP file, I investigated the attacker's MAC address, analyzed network communication, and identified a potential Man-in-the-Middle attack.

I also examined the captured data to identify a downloaded employee information file, retrieve relevant employee details, and determine the SSH password associated with the Domain Administrator.

Overall, this challenge strengthened my understanding of ARP, network traffic interception, and the importance of protecting sensitive information transmitted across internal networks.

<h2>9. Lessons Learned</h2>

- Learned how to examine Ethernet frames and identify MAC addresses.
- Improved my understanding of ARP and IP-to-MAC address resolution.
- Learned how ARP-related activity can be associated with Man-in-the-Middle attacks.
- Practiced investigating network communication between internal hosts.
- Learned how packet captures can contain evidence of transferred files.
- Practiced examining file contents to extract relevant information.
- Improved my understanding of how sensitive credentials can become exposed through insecure communication.
- Recognized the importance of network monitoring and secure authentication practices.
- Gained additional experience investigating network security incidents through packet analysis.

<h2>10. Evidence</h2>

| Screenshot | Description |
| --- | --- |
| 01-pcap-overview.png | Initial inspection of the provided PCAP file |
| 02-mac-address.png | Ethernet address information associated with the attacker |
| 03-arp-analysis.png | ARP traffic examination |
| 04-mitm-analysis.png | Network traffic supporting the MitM investigation |
| 05-file-identification.png | Identification of the downloaded CSV file |
| 06-employee-information.png | Employee information showing the department |
| 07-ssh-analysis.png | Captured communication associated with SSH credentials |

<h2>11. References</h2>

- Wireshark Documentation
- Wireshark Display Filter Reference
- tcpdump Manual
- RFC 826 – An Ethernet Address Resolution Protocol
- RFC 4253 – The Secure Shell (SSH) Transport Layer Protocol

---

Documented as part of my hands-on network traffic analysis and cybersecurity learning activities.
