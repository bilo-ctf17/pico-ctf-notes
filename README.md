# 🛡️ Cybersecurity CTF Proof of Work & Writeups Portfolio

[![PicoCTF Profile](https://img.shields.io/badge/PicoCTF-Profile-orange?style=for-the-badge&logo=picoctf)](https://picoctf.org)
[![CTFtime](https://img.shields.io/badge/CTFtime-Profile-red?style=for-the-badge&logo=ctftime)](https://ctftime.org)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=for-the-badge&logo=linkedin)](https://linkedin.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

Welcome to my **Capture The Flag (CTF) & Cybersecurity Proof of Work Repository**. 
This repository serves as a centralized, structured portfolio showcasing my problem-solving skills, hands-on experience, technical writeups, and automated exploit scripts across **PicoCTF** and other major CTF platforms (*HackTheBox, TryHackMe, CTFtime events*).

---

## 👨‍💻 About Me & Technical Summary

- **Primary Focus**: Offensive Security, Reverse Engineering, Vulnerability Research, and Cryptanalysis.
- **Goal**: Demonstrating practical cybersecurity competence through thorough documentation, clean code, and reproducible PoCs.
- **Key Technical Proficiencies**:
  - **Languages**: Python, C/C++, Bash, Assembly (x86/x64), JavaScript, SQL.
  - **Reverse Engineering & Pwn**: Ghidra, GDB + GEF/Pwnbg, IDA Pro, Radare2, `pwntools`.
  - **Forensics & PCAP**: Volatility, Wireshark, tshark, ExifTool, Binwalk, Stegsolve.
  - **Web Security**: Burp Suite, OWASP ZAP, SQLMap, Custom exploit payloads (SQLi, XSS, SSRF, LFI, JWT).
  - **Cryptography**: RSA attacks, AES modes, SageMath, Hashcat, John the Ripper.

---

## 📂 Repository Directory Structure

```text
.
├── README.md                      # Main portfolio dashboard & challenge tracker
├── docs/
│   └── WRITEUP_TEMPLATE.md        # Standardized professional writeup template
├── 01-General-Skills/             # Bash, scripting, encoding, CLI tools
├── 02-Web-Exploitation/           # Web vulnerabilities (SQLi, XSS, CSRF, JWT, LFI)
├── 03-Cryptography/               # Ciphers, RSA, ECC, Hashing, SageMath scripts
├── 04-Reverse-Engineering/        # Binary analysis, Ghidra decompilation, decompilers
├── 05-Forensics/                  # Memory dumps, PCAP analysis, Steganography, Disk images
├── 06-Binary-Exploitation/        # Buffer overflows, ROP, Format Strings, Heap, Shellcode
├── 07-OSINT/                      # Open Source Intelligence & Geolocation challenges
└── 08-Misc/                       # Esoteric languages, Game Hacking, AI/ML CTFs
```

---

## 📊 Challenge Solves & Proof of Work Matrix

> *The table below tracks documented challenge writeups, difficulty, key concepts, and solution scripts.*

| ID | Platform | Category | Challenge Name | Difficulty | Key Concepts / Vulnerabilities | Writeup & Script |
|:---|:---|:---|:---|:---:|:---|:---:|
| 001 | PicoCTF | Web Exploitation | [Inspect HTML](./02-Web-Exploitation/PicoCTF/Inspect-HTML/) | `Easy` | Source inspection, HTTP Headers | [Writeup](./02-Web-Exploitation/PicoCTF/Inspect-HTML/README.md) \| [Script](./02-Web-Exploitation/PicoCTF/Inspect-HTML/solve.py) |
| 002 | PicoCTF | Reverse Engineering | [Vault-Door-1](./04-Reverse-Engineering/PicoCTF/Vault-Door-1/) | `Medium` | Java Bytecode, String manipulation | [Writeup](./04-Reverse-Engineering/PicoCTF/Vault-Door-1/README.md) \| [Script](./04-Reverse-Engineering/PicoCTF/Vault-Door-1/solve.py) |
| 003 | PicoCTF | Cryptography | [RSA-Pop-Quiz](./03-Cryptography/PicoCTF/RSA-Pop-Quiz/) | `Medium` | RSA Math, Euler Totient, SageMath | [Writeup](./03-Cryptography/PicoCTF/RSA-Pop-Quiz/README.md) \| [Script](./03-Cryptography/PicoCTF/RSA-Pop-Quiz/solve.py) |
| 004 | PicoCTF | Binary Exploitation | [buffer overflow 1](./06-Binary-Exploitation/PicoCTF/buffer-overflow-1/) | `Hard` | EIP Overwrite, `pwntools`, Ret2Win | [Writeup](./06-Binary-Exploitation/PicoCTF/buffer-overflow-1/README.md) \| [Script](./06-Binary-Exploitation/PicoCTF/buffer-overflow-1/solve.py) |
| 005 | PicoCTF | Forensics | [Wireshark-two](./05-Forensics/PicoCTF/Wireshark-two/) | `Medium` | PCAP Analysis, DNS Exfiltration | [Writeup](./05-Forensics/PicoCTF/Wireshark-two/README.md) \| [Script](./05-Forensics/PicoCTF/Wireshark-two/solve.py) |

---

## 🎯 Category Breakdown & Skill Showcase

### 1. 🧰 General Skills (`01-General-Skills/`)
Focuses on Linux CLI fluency, Python scripting automation, data encoding/decoding (Base64, Hex, XOR), and fundamental networking concepts.

### 2. 🌐 Web Exploitation (`02-Web-Exploitation/`)
Demonstrates understanding of web architecture, OWASP Top 10 vulnerabilities, authentication bypasses, SSRF, SQL Injection, Cross-Site Scripting (XSS), and API security.

### 3. 🔐 Cryptography (`03-Cryptography/`)
Contains mathematical cryptanalysis, breakdown of broken ciphers, RSA weak key attacks, AES mode misconfigurations (ECB/CBC oracle attacks), and custom Python/SageMath solvers.

### 4. ⚙️ Reverse Engineering (`04-Reverse-Engineering/`)
Showcases static and dynamic analysis of binaries (x86, x64, ARM, Java `.class`, Python `.pyc`). Features Ghidra/IDA annotations, control-flow analysis, and keygenning.

### 5. 🔍 Forensics (`05-Forensics/`)
Covers digital investigation, memory analysis via Volatility, packet inspection via Wireshark/tshark, file system carving, metadata analysis, and steganography decoding.

### 6. 💥 Binary Exploitation (`06-Binary-Exploitation/`)
Focuses on memory corruption bugs: Stack-based buffer overflows, Return-Oriented Programming (ROP), Format String vulnerabilities, Shellcoding, Heap exploitation, and bypassing modern mitigations (ASLR, NX, Canary, PIE).

---

## 📑 Standard Writeup Structure & Quality Standard

Every challenge folder in this portfolio follows a consistent schema:
1. `README.md` - Complete writeup formatted using [`WRITEUP_TEMPLATE.md`](./docs/WRITEUP_TEMPLATE.md).
2. `solve.py` / `solve.sh` - Fully automated, reproducible solution script (using `pwntools`, `requests`, `scapy`, etc.).
3. `assets/` - Relevant screenshots, original challenge files, PCAPs, or disassembled snippets.

---

## 📮 Contact & Professional Links

- **GitHub**: [Your Github Username](https://github.com/)
- **LinkedIn**: [Your LinkedIn Profile](https://linkedin.com/in/)
- **Email**: `your.email@example.com`
- **PicoCTF Username**: `[Your Username]`
