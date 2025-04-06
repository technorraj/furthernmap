# TryHackMe: Further Nmap Walkthrough

This walkthrough provides a comprehensive guide to completing the [Further Nmap](https://tryhackme.com/room/furthernmap) room on TryHackMe. The room explores advanced features of Nmap, a powerful network scanning tool, and covers various scanning techniques, switches, and practical applications.

---

## Table of Contents

- [Task 1: Deploy](#task-1-deploy)
- [Task 2: Introduction](#task-2-introduction)
- [Task 3: Nmap Switches](#task-3-nmap-switches)
- [Task 4: Scan Types](#task-4-scan-types)
  - [TCP Connect Scans](#tcp-connect-scans)
  - [SYN Scans](#syn-scans)
  - [UDP Scans](#udp-scans)
  - [NULL, FIN, and Xmas Scans](#null-fin-and-xmas-scans)
  - [ICMP Network Scanning](#icmp-network-scanning)
- [Task 5: Nmap Scripting Engine (NSE)](#task-5-nmap-scripting-engine-nse)
  - [Working with the NSE](#working-with-the-nse)
  - [Searching for Scripts](#searching-for-scripts)
- [Task 6: Firewall Evasion Techniques](#task-6-firewall-evasion-techniques)
- [Task 7: Practical](#task-7-practical)
- [Task 8: Conclusion](#task-8-conclusion)

---

## Task 1: Deploy

**Objective:** Deploy the attached VM.

**Action:** Start the virtual machine provided with the room. This VM will serve as the target for your Nmap scans throughout the tasks.

---

## Task 2: Introduction

**Q1:** What networking constructs are used to direct traffic to the right application on a server?  
**A1:** Ports

**Q2:** How many of these are available on any network-enabled computer?  
**A2:** 65535

**Q3:** [Research] How many of these are considered "well-known"?  
**A3:** 1024

**Explanation:** Ports are numerical identifiers in networking used to distinguish different services or applications running on a single device. There are 65,535 ports available, numbered from 0 to 65,535. The first 1,024 ports (0-1023) are designated as "well-known" ports and are typically assigned to widely used protocols and services.

---

## Task 3: Nmap Switches

Nmap offers a variety of command-line switches to customize scans. Below are some commonly used switches:

- **`-sS`**: Performs a TCP SYN scan (also known as a half-open scan).
- **`-sU`**: Performs a UDP scan.
- **`-O`**: Enables OS detection.
- **`-sV`**: Enables version detection.
- **`-v`**: Increases verbosity level. Use `-vv` for even more verbosity.
- **`-oA <basename>`**: Outputs results in all formats (normal, XML, and grepable).
- **`-oN <filename>`**: Outputs results in normal format.
- **`-oG <filename>`**: Outputs results in grepable format.
- **`-A`**: Enables aggressive scan options, including OS detection, version detection, script scanning, and traceroute.
- **`-T<0-5>`**: Sets the timing template (higher is faster but more detectable).
- **`-p <port(s)>`**: Specifies ports to scan. Use `-p-` to scan all 65,535 ports.
- **`--script <script>`**: Executes a specific NSE script.
- **`--script=<category>`**: Executes all scripts in a specified category.

---

## Task 4: Scan Types

Nmap supports various scan types, each with its own use cases:

### TCP Connect Scans

**Q1:** Which RFC defines the appropriate behavior for the TCP protocol?  
**A1:** RFC 793

**Q2:** If a port is closed, which flag should the server send back to indicate this?  
**A2:** RST (Reset)

**Explanation:** A TCP Connect Scan completes the three-way handshake with each target port. If the port is closed, the server responds with a TCP packet with the RST flag set.

### SYN Scans

**Q1:** There are two other names for a SYN scan, what are they?  
**A1:** Half-open, Stealth

**Q2:** Can Nmap use a SYN scan without Sudo permissions (Y/N)?  
**A2:** N

**Explanation:** SYN scans, also known as half-open or stealth scans, send SYN packets and wait for responses without completing the handshake. They require sudo permissions to execute.

### UDP Scans

**Q1:** If a UDP port doesn’t respond to an Nmap scan, what will it be marked as?  
**A1:** open|filtered

**Q2:** When a UDP port is closed, by convention the target should send back a "port unreachable" message. Which protocol would it use to do so?  
**A2:** ICMP

**Explanation:** UDP scans send UDP packets to target ports. If there is no response, the port is marked as open|filtered. If the port is closed, the target responds with an ICMP Port Unreachable message.

### NULL, FIN, and Xmas Scans

**Q1:** Which of the three shown scan types uses the URG flag?  
**A1:** Xmas

**Q2:** Why are NULL, FIN, and Xmas scans generally used?  
**A2:** Firewall evasion

**Q3:** Which common OS may respond to a NULL, FIN, or Xmas scan with a RST for every port?  
**A3:** Microsoft Windows

**Explanation:** These scans manipulate TCP flags to evade basic firewall rules. The Xmas scan sets the PSH, URG, and FIN flags. Microsoft Windows systems typically respond with a RST for every port when subjected to these scans.

### ICMP Network Scanning

**Q1:** How would you perform a ping sweep on the 172.16.x.x network (Netmask: 255.255.0.0) using Nmap? (CIDR notation)  
**A1:** `nmap -sn 172.16.0.0/16`

**Explanation:** ICMP scans are used to discover live hosts on a network. The `-sn` switch tells Nmap to perform a ping sweep without port scanning.

---

## Task 5: Nmap Scripting Engine (NSE)

The Nmap Scripting Engine allows users to write and share scripts to automate networking tasks.

**Q1:** What language is used to write NSE scripts?  
**A1:** Lua

**Q2:** What category of scripts is considered intrusive?  
**A2:** intrusive

**Q3:** What option can you use to set script arguments?  
**A3:** `0
