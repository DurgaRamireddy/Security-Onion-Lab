# Security-Onion-Lab

## Introduction
In this lab, I explored Security Onion tools by individually installing Zeek and Suricata, as I was unable to install the full Security Onion suite. Both tools are widely used for network monitoring and intrusion detection. I analyzed network traffic using PCAP files to understand their functionality and effectiveness.

## Tools Used
  - **Zeek** – Open-source network monitoring and traffic analysis tool
  - **Suricata** – Network IDS/IPS and NSM engine
  - **PCAP files** – id1.cn-inject.pcap dataset for traffic analysis
  - **Linux environment** – Ubuntu/Kali
## Lab Workflow
**1. Zeek**
**Description:**
- Deep-inspects packets and logs network activity (connections, HTTP requests, DNS lookups, file transfers).
- Useful for both real-time monitoring and historical analysis.

**Dataset:**
- id1.cn-inject.pcap

**Results:**
- Ran zeek -r id1.cn-inject.pcap and generated detailed logs:
   - conn.log: Connection between 172.20.6.1 → 42.96.141.35 over TCP 80, showing a large byte transfer difference suggesting possible data exfiltration.
   - http.log: Showed HTTP traffic, URIs, user-agents, and referrers.
   - files.log & packet_filter.log: Captured file activity and metadata (MIME types, sizes), useful for malware or forensic analysis.
 
**2. Suricata**
**Description:**
- IDS/IPS/NSM engine capable of real-time traffic analysis.
- Detects known threats using signatures and supports deep packet inspection.

**Dataset:**
- Same PCAP file (id1.cn-inject.pcap)

**Results:**
- Ran sudo suricata -r id1.cn-inject.pcap -l output/ and generated logs:
  - eve.json: High-level alert data including HTTP method, hostname, and payload fingerprint.
  - fast.log: Human-readable alerts; Suricata triggered 2 alerts matching known threat patterns.
  - stats.log: Performance stats; processed 9 packets in 0.15 seconds without errors.

**Key Learning:**
    Suricata is ideal for real-time alerting and signature-based detection, while Zeek excels at deep packet inspection and behavioral analysis. Together, they provide robust network monitoring and investigation capabilities.

## Verification of Tool Installation
- Verified both Zeek and Suricata could successfully process PCAP files and generate relevant logs.
- Successful log generation confirms legitimate installation and functioning of the tools.

## Skills Demonstrated
- PCAP File Analysis
- Network Security Monitoring (NSM)
- Intrusion Detection System (IDS) Analysis
- Zeek Log Analysis (conn.log, http.log, files.log)
- Suricata Alert Analysis (eve.json, fast.log)
- Signature-Based Threat Detection

## Conclusion
Zeek provides detailed network metadata, while Suricata detects security events and alerts. Even without the full Security Onion suite, these two tools allow for network monitoring, threat detection, and traffic analysis, demonstrating core skills in cybersecurity operations and incident investigation.

## Author
Durga Sai Sri Ramireddy </br>
Master's student - Cybersecurity </br?
University Of Houston

*This project was developed as part of academic coursework and expanded for cybersecurity portfolio demonstration.*
