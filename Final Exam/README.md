# COMP 5350: Final Exam
### Author: Blake Senn 
### Course: Digital Forensics

Project Overview

This final exam required a full-scope digital forensic investigation of a compromised system. The objective was to analyze multiple evidence sources—including Windows Registry hives, network packet captures, and disk artifacts—to reconstruct the attack lifecycle. The investigation focused on identifying the threat actor's entry point, mapping their lateral movement, locating malicious payloads, and determining if any sensitive data was exfiltrated.

Tools Used
- RegRipper (Registry analysis)
- Wireshark (Network traffic analysis)
- ExifTool (Metadata inspection)
- Stegseek (Steganography analysis)
- Hashcalc / md5sum (File integrity verification)

Methodology
1. System & User Profiling (Q1): Analyzed the SYSTEM, SOFTWARE, and NTUSER.DAT registry hives to establish the system's baseline configuration, install date, and user activity logs.
2. Network Intrusion Detection (Q2): Examined the provided PCAP file to isolate suspicious traffic, identifying the attacker's IP address and the specific exploit vector used to gain access.
3. Payload Isolation (Q3): Reconstructed TCP streams from the network capture to recover and identify the malicious payload dropped onto the victim machine.
4. Data Exfiltration Analysis (Q4): Investigated potential steganography and hidden data channels to determine if sensitive files were stolen or concealed within other artifacts.
5. Timeline Reconstruction (Q5): Correlated timestamps across registry keys, file system metadata, and network logs to build a definitive timeline of the compromise.

Key Findings 
Question 1: Registry Forensics
- System Profile: Identified the Operating System install date and the current timezone offset.
- User Attribution: Determined the last user to successfully log in and the specific timestamp of that event, establishing the timeline of authorized vs. unauthorized access.

Question 2: Network Forensics
- Attacker Identification: Isolated the attacker's IP address and the specific port used for the initial connection.
- Exploit Vector: Identified the method of intrusion, confirming whether it was a brute-force attack or an exploit of a vulnerable service.

Question 3: Payload Analysis
- Malware Recovery: Successfully recovered the malicious executable from the network stream.
- Payload Identification: Verified the file's hash and identified its function (e.g., reverse shell or keylogger) based on its behavior and signature.

Question 4: Data Exfiltration
- Hidden Data: Discovered a hidden file concealed within a cover image using steganography.
- Stolen Assets: Decoded the hidden content to reveal the sensitive information targeted by the attacker.

Question 5: Incident Timeline
- Compromise Window: Established the exact start and end times of the attack based on the correlation of network and registry artifacts.
- Sequence of Events: Mapped the attacker's actions from initial scan to final data exfiltration.

Recovered Evidence 
The following artifacts were recovered and verified during the investigation:
- Registry Reports: Parsed outputs from SYSTEM and NTUSER.DAT.
- Malicious Payload: The executable file recovered from the network stream.
- Exfiltrated Data: The decoded file containing the stolen information.
- Steganography Carrier: The original image file used to hide the stolen data.
- Network Logs: Filtered PCAP files isolating the attacker's traffic.
