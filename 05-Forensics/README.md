# 🔍 Digital Forensics & Incident Response

Digital Forensics challenges involve analyzing memory dumps, network traffic packet captures (PCAPs), corrupted file systems, steganography, and file metadata.

## 📌 Subdirectories & Challenges

| Challenge Name | Platform | Difficulty | Key Concepts | Link |
|:---|:---|:---:|:---|:---:|
| Wireshark-two | PicoCTF | Medium | PCAP Analysis, DNS Data Exfiltration | [View](./PicoCTF/Wireshark-two/) |

## 🛠️ Essential Tools

- **Wireshark & TShark**: Network packet capture analysis & extraction
- **Volatility 2 / Volatility 3**: RAM / Memory dump forensics
- **Binwalk**: Firmware extraction & embedded file carving (`binwalk -e file`)
- **ExifTool**: Metadata inspection (`exiftool image.png`)
- **Stegsolve / zsteg**: Image steganography solver
- **Autopsy**: Full disk image forensics & timeline analysis
