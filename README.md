# Task 1: Scan Your Local Network for Open Ports

## About
This repository contains the results of a basic Nmap TCP SYN scan and the corresponding Wireshark packet capture.

## Files Included
- `scan_results.txt` – Nmap scan output for the network `10.0.2.0/24`.
- `nmap_scan_capture.pcapng` – Packet capture recorded during the scan.

## Tools Used
- **Nmap** – for scanning open ports and services.
- **Wireshark** – for analyzing network traffic.

## How to View
- Open `scan_results.txt` in any text editor.
- Open `nmap_scan_capture.pcapng` using Wireshark.
## 🔐 What I Learned – Risk Analysis of Open Ports

During the scan, I identified several open ports on local hosts. Here's what I learned about their associated risks:

| Port | Service       | Risk Level | 
|------|---------------|------------|
| 135  | msrpc         | ⚠️ High     | 
| 445  | microsoft-ds  | ⚠️ High     | 
| 1042 | afrog         | ❓ Unknown  | 
| 1043 | boinc         | ⚠️ Medium   | 
| 7070 | realserver    | ⚠️ Medium   | 
| 7778 | interwise     | ⚠️ Medium   | 
| 8080 | http-proxy    | ⚠️ Medium   | 
| 53   | domain (DNS)  | ⚠️ Medium   | 

## 📊 Packet Capture Analysis (Optional – with Wireshark)

The file `nmap_scan_capture.pcapng` was opened using **Wireshark** to observe traffic generated during the Nmap TCP SYN scan.

### Key Observations:
- Each SYN packet sent by Nmap to various ports was followed by a **SYN-ACK** if the port was open (indicating a responsive service).
- Closed ports typically responded with **RST** (Reset) packets.
- Some filtered ports showed **no response**, which could be due to firewalls or packet filtering mechanisms.
- The presence of **SYN → SYN-ACK** handshakes confirmed service availability on specific ports (e.g., 135, 445, 53, 8080).

Analyzing the packet capture allowed verification of the Nmap scan results at a **packet level**, which is useful for detecting IDS/IPS responses, latency, or unusual packet behavior.


