# TryHackMe: Further Nmap - Walkthrough

This is a complete walkthrough for the TryHackMe room [Further Nmap](https://tryhackme.com/room/furthernmap). It covers all 15 tasks, focusing on advanced scanning techniques, Nmap switches, script usage, and firewall evasion methods.

---

## Task 2: Introduction

**Q:** What networking constructs are used to direct traffic to the right application on a server?  
**A:** Ports

**Q:** How many of these are available on any network-enabled computer?  
**A:** 65535

**Q:** How many of these are considered "well-known"?  
**A:** 1024

---

## Task 3: Nmap Switches

**Q:** What is the first switch listed in the help menu for a SYN scan?  
**A:** -sS

**Q:** Which switch would you use for a UDP scan?  
**A:** -sU

**Q:** Which switch detects the operating system?  
**A:** -O

**Q:** Which switch detects the version of services?  
**A:** -sV

**Q:** How to increase verbosity?  
**A:** -v

**Q:** How to set verbosity level to two?  
**A:** -vv

**Q:** Save results in all formats?  
**A:** -oA

**Q:** Save results in normal format?  
**A:** -oN

**Q:** Save results in grepable format?  
**A:** -oG

**Q:** Enable aggressive mode?  
**A:** -A

**Q:** Set timing template to level 5?  
**A:** -T5

**Q:** Scan only port 80?  
**A:** -p 80

**Q:** Scan ports 1000–1500?  
**A:** -p 1000-1500

**Q:** Scan all ports?  
**A:** -p-

**Q:** Activate a script from the library?  
**A:** --script

**Q:** Activate all scripts in the "vuln" category?  
**A:** --script=vuln

---

## Task 5: TCP Connect Scans

**Q:** Which RFC defines appropriate TCP behavior?  
**A:** RFC 793

**Q:** If a port is closed, which flag is returned?  
**A:** RST

---

## Task 6: SYN Scans

**Q:** What are two other names for a SYN scan?  
**A:** Half-open, Stealth

**Q:** Can Nmap perform SYN scans without sudo?  
**A:** No

---

## Task 7: UDP Scans

**Q:** If a UDP port doesn’t respond, what is it marked as?  
**A:** open|filtered

**Q:** Which protocol is used to send a “port unreachable” message?  
**A:** ICMP

---

## Task 8: NULL, FIN, and Xmas Scans

**Q:** Which scan type uses the URG flag?  
**A:** Xmas

**Q:** Why are these scans used?  
**A:** Firewall evasion

**Q:** Which OS may respond with RST for every port?  
**A:** Microsoft Windows

---

## Task 9: ICMP Network Scanning

**Q:** How would you perform a ping sweep on the 172.16.x.x network (Netmask: 255.255.0.0)?  
**A:** `nmap -sn 172.16.0.0/16`

---

## Task 10: NSE Scripts Overview

**Q:** What language are NSE scripts written in?  
**A:** Lua

**Q:** Which script category is unsafe for production environments?  
**A:** intrusive

---

## Task 11: Working with the NSE

**Q:** What optional argument can the `ftp-anon.nse` script take?  
**A:** maxlist

---

## Task 12: Searching for Scripts

**Q:** Script that determines the OS of the SMB server?  
**A:** smb-os-discovery.nse

**Q:** What does this script depend on?  
**A:** smb-brute

---

## Task 13: Firewall Evasion

**Q:** Which protocol is often blocked, requiring use of `-Pn`?  
**A:** ICMP

**Q:** Which switch appends random data to packets?  
**A:** --data-length

---

## Task 14: Practical

**Q:** Does the target respond to ICMP requests?  
**A:** No

**Q:** Xmas scan on first 999 ports — how many are open or filtered?  
**A:** 999

**Q:** Reason for this result?  
**A:** No Response

**Q:** SYN scan on first 5000 ports — how many are open?  
**A:** 5

**Q:** Can Nmap log in anonymously to the FTP server (port 21)?  
**A:** Yes

---

## Task 15: Conclusion

This concludes the walkthrough of the "Further Nmap" room. The room explores advanced Nmap techniques including scanning types, timing templates, firewall evasion, NSE script usage, and more. This foundational knowledge is essential for penetration testers and security analysts to efficiently enumerate and assess systems.

---

**Room Link:** [https://tryhackme.com/room/furthernmap](https://tryhackme.com/room/furthernmap)  
**Author:** [technor_raj]
