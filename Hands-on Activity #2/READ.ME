# COMP 5350: NTFS Forensic Analysis & Steganography

[cite_start]**Author:** Blake Senn [cite: 177]
[cite_start]**Course:** Digital Forensics [cite: 175]

## Project Overview
This project documents the manual forensic analysis of the disk image `ShadowLaptop.dd`. [cite_start]Following the capture of the hacker "Ghost," investigators recovered a laptop belonging to his partner, "Shadow1"[cite: 309, 310, 312]. [cite_start]The objective was to locate partitions, recover hidden files, and decode steganographic messages to find the suspect's location[cite: 182, 313].

**Constraint:** All file recovery was performed manually using `dd`. [cite_start]No automated forensic suites were used[cite: 326].

## Tools Used
* [cite_start]`fdisk` / `mmls` (Partition analysis) [cite: 208]
* [cite_start]`dd` (Manual file carving) [cite: 274]
* [cite_start]`hexdump` (Hex analysis and signature verification) [cite: 211]
* [cite_start]`steghide` (Steganography extraction) [cite: 187]
* [cite_start]`base64` (Decoding encoded strings) [cite: 223]

## Methodology
1.  [cite_start]**Partition Discovery:** Identified a single NTFS partition starting at sector 2048[cite: 209].
2.  [cite_start]**Artifact Recovery:** Manually calculated byte offsets to carve files using `dd`[cite: 248].
3.  [cite_start]**Steganography Analysis:** Identified appended data in a JPEG file and used a recovered passphrase to extract hidden text[cite: 243, 244].

## Recovered Evidence
* [cite_start]**for_ghost.txt**: A text file carved from offset 13260 containing a clue referencing steganography[cite: 265, 281].
* **innocent_cat.jpg**: A JPEG image carved from offset 133120. Analysis revealed 2,992 bytes of hidden data appended after the EOF marker[cite: 264, 243].
* **passphrase.txt**: A text file carved from offset 133248 containing a Base64 string that decoded to the password "1234"[cite: 266, 282].
* **secret.txt**: A hidden file extracted from `innocent_cat.jpg` using `steghide`. [cite_start]It contained the suspect's real name (Sean) and address[cite: 244].

## Example Commands
**Manual File Carving:**
```bash
# Recovering innocent_cat.jpg (Offset: 133120 sectors, Size: 120 sectors)
[cite_start]dd if=ShadowLaptop.dd of=innocent_cat.jpg bs=512 skip=133120 count=120 status=progress [cite: 215]
