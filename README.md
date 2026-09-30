# Network-Sniffer
Cybersecurity internship project: Python + Scapy based network sniffer for capturing and analyzing network packets, protocols, ports, and basic payload information.
# 🔍 Basic Network Sniffer

A Python-based network packet sniffer developed using **Scapy** as part of a Cybersecurity Internship project. The project demonstrates how network traffic can be captured, inspected, and analyzed to understand fundamental network communication and protocol behavior.

## 📌 Project Overview

Network communication consists of packets traveling between different systems. Understanding these packets is an important foundation for cybersecurity, network monitoring, and incident analysis.

This project captures network packets from a selected network interface and extracts useful information such as:

- Source IP address
- Destination IP address
- Network protocol
- Source and destination ports
- Packet size
- Basic payload information
- Packet capture timestamps

Captured traffic can also be stored in **PCAP format** for further analysis using tools such as Wireshark.

---

## 🎯 Objectives

The main objectives of this project are:

1. Understand how network packets are structured.
2. Capture live network traffic using Python and Scapy.
3. Identify common protocols such as TCP, UDP, and ICMP.
4. Extract source and destination IP addresses.
5. Identify TCP/UDP port information.
6. Inspect basic packet payload data.
7. Store captured traffic in PCAP format.
8. Perform offline packet analysis.
9. Understand the relationship between network protocols and cybersecurity monitoring.

---

## 🧠 Deep Technical Understanding

A network packet can be viewed as a collection of protocol layers.

Typical communication can be represented as:

```text
Application Data
       ↓
   TCP / UDP
       ↓
      IP
       ↓
   Ethernet
       ↓
   Network
For example, an ICMP ping packet generally contains:
Ethernet
   ↓
IPv4
   ↓
ICMP
Whereas a TCP-based connection may contain:
Ethernet
   ↓
IPv4
   ↓
TCP
   ↓
Application Data
The sniffer examines these layers using Scapy and extracts relevant fields for analysis.
🔬 Packet Analysis
For every IP packet, the program attempts to identify:
Field
Description
Source IP
System that sent the packet
Destination IP
System receiving the packet
Protocol
TCP, UDP, ICMP, etc.
Source Port
Port used by the sender
Destination Port
Port used by the receiver
Packet Size
Total packet size in bytes
Payload
Data carried by the packet
Timestamp
Approximate packet observation time
🛠️ Technologies Used
Python 3
Scapy
Kali Linux
Wireshark
TCP/IP Networking
PCAP
📂 Project Structure
network-sniffer/
│
├── sniffer.py          # Captures and displays network packets
├── analyze.py          # Performs offline packet analysis
├── capture.pcap        # Captured packet data
├── README.md           # Project documentation
└── web/                # Local test environment
    └── index.html
⚙️ Installation
1. Clone the repository
git clone <YOUR-GITHUB-REPOSITORY-URL>
cd network-sniffer
2. Install Scapy
sudo apt update
sudo apt install python3-scapy -y
Verify the installation:
python3 -c "from scapy.all import *; print('Scapy OK')"
🚀 Usage
Identify the network interface
ip -br addr
Example:
eth0     UP     10.0.2.15/24
Update the interface in sniffer.py:
INTERFACE = "eth0"
Start packet capture
sudo python3 sniffer.py
The program displays information such as:
============================================================
Time        : 23:59:58
Source IP   : 10.0.2.15
Destination : 163.70.146.60
Protocol    : TCP
Packet Size : 54 bytes
Source Port : 52386
Dest Port   : 443
Payload     : None
💾 Saving Packets
Captured packets can be stored as a PCAP file:
wrpcap("capture.pcap", packets)
The PCAP file can later be analyzed with Scapy or Wireshark.
🔎 Offline Analysis
Run:
python3 analyze.py
Example output:
======================================================================
PACKET ANALYSIS
======================================================================
Total Packets: 30

001 | 10.0.2.15 -> 10.0.2.2 | ICMP | 84 bytes
002 | 10.0.2.2  -> 10.0.2.15 | ICMP | 84 bytes
003 | 10.0.2.15 -> 10.0.2.2 | ICMP | 84 bytes
🌐 Protocols Observed
TCP
TCP is a connection-oriented transport protocol.
Common applications include:
HTTPS
HTTP
SSH
Web applications
Example:
Source Port      → 52386
Destination Port → 443
Protocol         → TCP
UDP
UDP is a connectionless transport protocol commonly used where low overhead and speed are important.
Examples include:
DNS
DHCP
NTP
ICMP
ICMP is commonly used for network diagnostics.
For example:
ping <gateway-ip>
generates ICMP traffic that can be observed by the sniffer.
🔐 Cybersecurity Relevance
Packet analysis is an important foundation for:
Network Security Monitoring
SOC Operations
Incident Response
Network Troubleshooting
Threat Detection
Digital Forensics
Intrusion Detection
A packet sniffer by itself does not determine whether traffic is malicious. Security analysts normally correlate packet information with additional context, logs, IDS/IPS alerts, endpoint telemetry, and known indicators.
🧪 Testing
The project was tested using controlled network traffic such as:
ping -c 5 <gateway-ip>
and a local HTTP server:
python3 -m http.server 8000
Traffic was then captured and analyzed using the Python sniffer and PCAP/Wireshark analysis.
⚠️ Ethical & Legal Considerations
This tool should only be used on networks and systems for which you have explicit authorization.
Do not capture or inspect network traffic belonging to other users or networks without permission.
For internship and learning purposes, testing should be performed in an authorized lab or on your own system.
📚 Key Learning Outcomes
Through this project, I gained practical understanding of:
Network packet structure
TCP/IP fundamentals
Packet capture techniques
Scapy packet manipulation and analysis
TCP, UDP and ICMP identification
IP and port analysis
Payload inspection
PCAP-based investigation
Wireshark-assisted packet analysis
Basic network security monitoring
👨‍💻 Project Context
Project: Basic Network Sniffer
Domain: Cybersecurity / Network Security
Environment: Kali Linux
Language: Python
Primary Library: Scapy
Project Type: Cybersecurity Internship Project
