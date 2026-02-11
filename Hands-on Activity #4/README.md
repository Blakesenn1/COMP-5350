# COMP 5350: Steganography & File Carving
### Author: Blake Senn
### Course: Digital Forensics

Project Overview
This project involved a forensic examination of digital media seized from a laptop suspected of being used to plan a high-value theft against Aurelia Bank. The investigation focused on analyzing two directories, /Recovered_Images and /Recovered_Documents, to uncover concealed operational details. The primary objective was to detect steganography, reconstruct hidden data, and identify the target, team, and timeline of the criminal operation.

Tools Used
- ExifTool (Metadata analysis) 
- Stegseek (Steganography brute-forcing) 
- xxd (Hex dump and file signature analysis) 
- file (File type verification) 

Methodology
1. Steganalysis: utilized stegseek with a dictionary attack (passphrases.txt) to brute-force password-protected image files (beach.jpg, lena.bmp, mountain.jpg, nyc.jpg) and extract hidden text fragments.
2. Decoding & Translation: Concatenated extracted text files and converted Hexadecimal, Octal, and Binary strings into ASCII to reveal operational clues and passwords.
3. File Carving & Deep Analysis: Analyzed SANS_Digital_Forensic.pdf at the bit level using xxd to identify an appended ZIP archive via its "PK" file signature.
4. File Extension Verification: Used the file command to identify that team.pdf was a spoofed Microsoft Excel spreadsheet, which was then renamed and analyzed.

Key Findings 

Part 1: Steganography & Map Reconstruction
- Hidden Fragments: Successfully recovered four map fragments from the suspect images using unique passwords (hide_me1, aubieKey, Falcon2023, Shelby0123) .
- Decoded Passphrases: Decoded the string "alpha123" from a hex payload in lena.bmp, which served as the master key for the hidden PDF archive.
- Operational Intelligence: Assembled the map fragments on a grid layout to reveal the geographic area of the operation.

Part 2: Hidden Archive & The Heist Plan
- Concealed Archive: Discovered and extracted a password-protected ZIP file hidden within SANS_Digital_Forensic.pdf.
- Target & Location: Identified the target as a Rolex Daytona Platinum Watch and the location as Aurelia Bank in Auburn at 12 Noon.
- Team Roster: Recovered a spoofed Excel file (team.xls) identifying the crew: Shadow (Leader), Ghost (Safe Cracker), Viper (Driver), and Hawk (Lookout) .
- Getaway Vehicle: Recovered an image of a Green Mustang with license plate EP68BLZ.

Recovered Evidence
The following artifacts were recovered and verified during the investigation:
- Map Fragments: beach.jpg.out, nyc.jpg.out, lena.bmp.out, mountain.jpg.out (Text files containing coordinates/clues).
- Decoded Passphrases: alpha123, blue-crate, For3nsiC!.
- location.txt: Confirmed the heist time and location.
- team.xls: The team roster and profit-sharing agreement (originally spoofed as team.pdf).
- Daytona_116506_Platinum_Platona_Baguette.jpg: Image of the target item.
- EP68BLZ.jpg: Image of the getaway vehicle.

Example Command 
The following command was used to brute-force the steganography on the beach image using the provided wordlist:

stegseek beach.jpg passphrases.txt
