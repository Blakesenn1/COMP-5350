# COMP 5350: NTFS Forensic Analysis & Steganography
### Author: Blake Senn 
### Course: Digital Forensics 

Project Overview
This project documents the manual forensic analysis of a disk image (ShadowLaptop.dd) recovered from a laptop linked to the "Shadow1" alias, a partner of the captured hacker "Ghost". The investigation focused on identifying partitions, recovering hidden files, and decoding steganographic messages to locate the suspect.

Constraint: All analysis and file recovery were performed manually using command-line tools. No automated forensic software was used.

Tools Used
- fdisk / mmls (Partition analysis) 
- dd (Manual file carving) 
- hexdump (Hexadecimal analysis and signature verification) 
- steghide (Steganography extraction) 
- base64 (Decoding encoded strings)

Methodology
1. Partition Discovery: Identified a single active NTFS partition starting at sector 2048.
2. Artifact Recovery: Manually calculated byte offsets to carve files using dd.
3. Steganography Analysis: Identified appended data in a JPEG file and used a recovered passphrase to extract hidden text.
4. Recovered Evidence Using manual carving and steganography techniques, the following files were recovered and analyzed:
  - for_ghost.txt: A text file carved from offset 13260 containing a clue referencing steganography.
  - innocent_cat.jpg: A JPEG image carved from offset 133120. Analysis revealed 2,992 bytes of hidden data appended after the EOF marker.
  - passphrase.txt: A text file carved from offset 133248 containing a Base64 string that decoded to the password "1234".
  - secret.txt: A hidden file extracted from innocent_cat.jpg using steghide. It contained the suspect's real name (Sean) and address.

Example Recovery Command
The following command was used to manually carve the JPEG file containing the hidden data:

dd if=ShadowLaptop.dd of=innocent_cat.jpg bs=512 skip=133120 count=120 status=progress
