# 🛡️ Cybersecurity CTF Proof of Work & Writeups Portfolio

[![PicoCTF Profile](https://img.shields.io/badge/PicoCTF-Profile-orange?style=for-the-badge&logo=picoctf)](https://learn.cylabacademy.org/users/billoctf)

Welcome to my **Capture The Flag (CTF) & Cybersecurity Proof of Work Repository**.
This repository serves as a centralized, structured portfolio showcasing my problem-solving skills, hands-on experience, technical writeups, and automated exploit scripts across **PicoCTF** and other major CTF platforms (*HackTheBox, TryHackMe, CTFtime events*).

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

## 🏆 Scoreboard & Progress

| Category | Solved | Points |
| :--- | :---: | :---: |
| 🧰 General Skills | 2 | 200 pts |
| 🌐 Web Exploitation | 0 | 0 pts |
| 🔐 Cryptography | 0 | 0 pts |
| ⚙️ Reverse Engineering | 0 | 0 pts |
| 🔍 Forensics | 0 | 0 pts |
| 💥 Binary Exploitation | 1 | 50 pts |
| **Total** | **3** | **250 pts** |

---

## 📊 Challenge Solves & Proof of Work Matrix

> *The table below tracks documented challenge writeups, difficulty, key concepts, and solution scripts.*

| ID | Platform | Category | Challenge Name | Points | Difficulty | Key Concepts / Vulnerabilities | Writeup & Script |
|:---|:---|:---|:---|:---:|:---:|:---|:---|
| 001 | PicoCTF | Binary Exploitation | [format-string-0](./06-Binary-Exploitation/format-string-0/) | 50 | `Easy` | Format Strings, Width Modifiers, Stack Dereferencing, SIGSEGV Signal Handler | [Writeup](./06-Binary-Exploitation/format-string-0/README.md) \| [Source](./06-Binary-Exploitation/format-string-0/format-string-0.c) |
| 002 | PicoCTF | General Skills | [Undo](./01-General-Skills/Undo/) | 100 | `Easy` | Base64 decoding, string reversal, tr mapping (ROT13) | [Writeup](./01-General-Skills/Undo/writeup.md) |
| 003 | PicoCTF | General Skills | [Bytemancy-1](./01-General-Skills/Bytemancy-1/) | 100 | `Easy` | Python input, ASCII representation, shell piping | [Writeup](./01-General-Skills/Bytemancy-1/writeup.md) \| [Source](./01-General-Skills/Bytemancy-1/app.py) |

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

- **GitHub**: [bilo-ctf17](https://github.com/bilo-ctf17)

- **PicoCTF Username**: `billoctf`
