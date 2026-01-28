# COMP 5350: Manual FAT16 Forensic Analysis
### Author: Blake Senn 
### Course: Digital Forensics

Project Overview
This project documents the manual forensic analysis of a disk image (captured_image_work.dd) recovered from a laptop linked to the APT99 cybercriminal group. The investigation focused on identifying partitions, recovering deleted data, and finding evidence of a bank heist.

Constraint: All analysis and file recovery were performed manually using command-line tools. No automated forensic software (like EnCase or Autopsy) was used.

Tools Used
- dd (Data extraction and carving)
- xxd / hexdump (Hexadecimal analysis)
- file (File type verification)
- unzip (Archive extraction)
- base64 (Decoding hidden strings)

Methodology
1. Partition Analysis: Identified two active FAT16 partitions in the Master Boot Record (MBR).
2. Offset Calculation: Used the BIOS Parameter Block (BPB) and Root Directory to manually calculate Start LBAs and sector counts.
3. File Carving: Extracted files bit-by-bit using dd based on the calculated offsets.
4. Content Analysis: Analyzed file headers and decoded content to reveal hidden passwords and target locations.

Recovered Evidence
- Using manual carving techniques, the following files were recovered and analyzed:
- email.log.odt: An active file containing communication logs. Analysis of the internal XML revealed a hidden password (Phantom$123).
- FINAL_PLAN.ZIP: A deleted file that was manually recovered. It contained the heist target location ("Old Warehouse, Dock 9, New York") which was decoded from a Base64 string.
- BANK.PNG: An active image file showing a compromised bank account interface.

Example Recovery Command
The following command was used to manually carve the deleted zip file:

dd if=captured_image.dd of=FINAL_PLAN.ZIP bs=512 skip=108696 count=3 status=progress
