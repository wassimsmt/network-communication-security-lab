Hands-on networking and security validation lab focused on understanding real traffic behavior and defensive controls.

# 🔐 Network Communication & Security Lab

## 🧭 Lab Architecture

             Host-Only Network

+---------------------+        Network Traffic        +----------------------+
|     Kali Linux      |  <------------------------->  |     Ubuntu Server    |
|   (Test / Attacker) |                               |      (Target)        |
|                     |                               |                      |
| - Nmap Scanning     |                               | - SSH Service (22)   |
| - Netcat Testing    |                               | - Nginx Web (80)     |
| - Traffic Analysis  |                               | - UFW Firewall       |
+---------------------+                               +----------------------+

Purpose:
- Validate network communication
- Analyze TCP behavior
- Apply firewall hardening

---

## 📌 Overview

This project demonstrates practical networking fundamentals and basic host hardening in a controlled virtual lab environment.

The objective was to understand how network communication works at a technical level and how security controls affect traffic flow. The lab focuses on validating exposed services, analyzing TCP behavior, and implementing firewall policies with measurable before-and-after results.

This project is part of my hands-on learning journey while studying networking and cybersecurity concepts.

---

## 🎯 Objectives

- Build a controlled lab environment using virtual machines
- Validate IP addressing and network connectivity
- Identify exposed services and listening ports
- Perform TCP and UDP network scanning
- Capture network traffic to observe TCP communication behavior
- Apply firewall hardening using UFW
- Verify security improvements through rescanning and logs
- Document methodology and findings professionally

---

## 🧪 Lab Environment

### Attacker Machine
- Kali Linux
- Tools used:
  - Nmap
  - Netcat
  - Curl

### Target Machine
- Ubuntu Server
- Services:
  - OpenSSH
  - Nginx Web Server
- Security Tools:
  - UFW Firewall
  - tcpdump

### Network Design

VirtualBox environment with:

- Host-only network (isolated lab communication)
- Optional NAT interface (for updates only)

---

## 🧠 Methodology

1️⃣ Validate network configuration

- Check IP addressing
- Confirm routing
- Verify connectivity

2️⃣ Baseline Assessment

- Identify listening services
- Perform TCP and UDP scans
- Document exposed attack surface

3️⃣ Traffic Analysis

- Capture packets using tcpdump
- Observe TCP handshake behavior

4️⃣ Security Hardening

- Configure UFW firewall
- Apply default deny inbound policy
- Allow only required services

5️⃣ Verification

- Re-scan target
- Compare before/after results
- Analyze firewall logs

---

## 📂 Project Structure

Network_Communication_Security_Lab/
│
├── README.md
├── scope.md
├── architecture.md
├── commands/
│ └── commands_used.md
├── scans/
│ ├── nmap_tcp_before.txt
│ ├── nmap_udp_before.txt
│ ├── nmap_tcp_after.txt
│ └── nmap_udp_after.txt
├── firewall/
│ ├── ufw_rules_after.txt
│ └── ufw_log_sample.txt
├── captures/
│ ├── tcpdump_handshake_http.txt
│ └── tcpdump_handshake_ssh.txt
└── screenshots/


---

## 🔍 Key Findings

- TCP and UDP scanning provide different visibility into services
- TCP reliability can be observed through SYN/SYN-ACK/ACK sequences
- Host firewall configuration significantly reduces attack surface
- Proper documentation makes technical work reproducible and verifiable

---

## 🧰 Skills Demonstrated

- Network configuration validation
- TCP/IP communication understanding
- Port and service analysis
- Network reconnaissance using Nmap
- Packet capture and analysis
- Firewall policy implementation
- Security documentation practices

---

## ⚠️ Disclaimer

This project was conducted in a fully isolated lab environment for educational purposes only. No real systems or external networks were targeted.

---

## 👤 Author

Wassim Abelghouch  

Cybersecurity Student | Aspiring Security Engineer

