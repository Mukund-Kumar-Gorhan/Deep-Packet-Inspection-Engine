# Deep-Packet-Inspection-Engine
This project performs OFFLINE packet inspection using PCAP files and does not capture or block live network traffic.


DPI Engine (Offline Deep Packet Inspection)
Overview

This project is an Offline Deep Packet Inspection (DPI) Engine built in C++. It analyzes network traffic stored in PCAP files, identifies applications and domains using packet inspection techniques, applies blocking rules, and generates a filtered output PCAP file.

The engine demonstrates core networking, packet parsing, flow tracking, TLS SNI extraction, application classification, and rule-based filtering concepts.

Note: This is an offline DPI engine. It does not monitor or block live network traffic. It only processes the packet data available inside the provided PCAP file.

Features
PCAP file parsing
Ethernet, IPv4, TCP, and UDP packet analysis
Five-tuple flow tracking
TLS SNI extraction
HTTP Host header extraction
Application identification
Domain detection
Rule-based blocking
Filtered PCAP generation
Traffic statistics and reporting
Multi-threaded processing architecture
How It Works
Input PCAP
     ↓
Packet Parsing
     ↓
Flow Identification
     ↓
SNI / Host Extraction
     ↓
Application Classification
     ↓
Rule Evaluation
     ↓
Allow / Block
     ↓
Output PCAP + Report
Important Limitation
Offline Processing Only

This project is designed for offline analysis.

It reads packets from:

input.pcap

and generates:

output.pcap

The engine does not capture live packets from a network adapter and does not block real-time traffic on a system.

For example:

If www.youtube.com exists inside the PCAP file, the engine can detect or block it.
If YouTube is currently open in your browser, this project will not block it because it is not connected to live network traffic.
Example Usage
Analyze Traffic
./dpi_simple test_dpi.pcap output.pcap
Block YouTube
./dpi_simple test_dpi.pcap output.pcap --block-app YouTube
Block Domain
./dpi_simple test_dpi.pcap output.pcap --block-domain facebook
Block IP
./dpi_simple test_dpi.pcap output.pcap --block-ip 192.168.1.50
Sample Output
Total Packets: 77
Forwarded: 69
Dropped: 8

Detected Applications:
- YouTube
- Facebook
- GitHub
- Google
- Instagram
- Telegram
- TikTok
Technologies Used
C++17
PCAP Processing
TCP/IP Networking
TLS SNI Inspection
Multi-threading
Hash-based Flow Tracking
Educational Purpose

This project was developed primarily for:

Learning computer networking
Understanding packet structures
Understanding DPI concepts
Learning traffic classification techniques
Exploring flow tracking and packet inspection
AI Usage Disclosure

Approximately 80% of this project was developed with the assistance of Artificial Intelligence tools.

AI was used to help with:

Code generation
Architecture design
Documentation
Debugging assistance
Networking concepts explanation

All generated code was reviewed, modified, tested, and integrated into the final project by the project author.

Future Improvements
Live packet capture using Npcap/libpcap
Real-time DPI processing
Firewall integration
QUIC/HTTP3 support
Web dashboard
Advanced rule management
Traffic visualization
Disclaimer

This project is intended for educational and research purposes only.

Use only on systems and network traffic that you own or have explicit authorization to analyze.
