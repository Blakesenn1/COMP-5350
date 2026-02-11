# COMP 5350: Windows Registry & Network Forensics
### Author: Blake Senn
### Course: Digital Forensics

Project Overview
This project consists of a two-part forensic investigation. Part 1 involved the analysis of Windows Registry hives to reconstruct system configurations and user activity. Part 2 focused on network forensics, analyzing a packet capture (FTPPackets.pcap) to investigate a data breach on an FTP server involving multiple threat actors and data exfiltration.

Tools Used
- RegRipper v3.0 (Registry analysis)
- Wireshark (Network traffic analysis)
- shasum / md5sum (File integrity verification)

Methodology
1. Registry Forensics: Used RegRipper plugins (samparse, run, ips, runmru) to parse the SAM, SOFTWARE, SYSTEM, and NTUSER.DAT hives.
2. Network Forensics: Applied Wireshark filters (ftp || ftp-data) to isolate control and data channels.
3. Stream Reconstruction: Used "Follow TCP Stream" to manually recover transferred files from the raw packet data.
4. Attack Reconstruction: Built a timeline of events based on login timestamps, IP addresses, and file transfer commands (RETR/STOR).

Key Findings
Part 1: Windows Registry
- User Activity: Identified the user 'aubie' and their last login time (Fri Oct 23 00:01:01 2020 Z).
- System Config: Located the system's static private IP address (192.168.48.141).
- Autostarts: Identified applications configured to run at startup, including VMware tools and OneDrive.

Part 2: Network Intrusion
- Authorized Access: Identified an initial valid login by ftpuser to download employee details.
- Unauthorized Access: Detected two attackers (johnsmith and janedoe) accessing the server from different IPs (172.19.201.228 and 131.204.27.177).
- Compromise & Exfiltration: The authorized user's machine was compromised, likely via a downloaded payload (documents.zip), and subsequently used to exfiltrate a sensitive file (Mortgage.pdf) to the attacker.

Recovered Evidence
The following files were recovered from the network traffic and verified using hashing tools:
- employee_details.txt: Authorized download.
- Check1.jpg & check1.jpg: Unauthorized upload and download.
- statement2.pdf & statement1.pdf: Unauthorized downloads.
- documents.zip: Presumed malware payload downloaded by the compromised victim.
- Mortgage.pdf: Sensitive data exfiltrated by the victim's compromised machine.

Example Command
The following RegRipper command was used to parse the SAM hive for user account information:

./rip.exe -r SAM -p samparse
