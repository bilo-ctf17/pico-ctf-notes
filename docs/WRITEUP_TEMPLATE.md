# Writeup: [Challenge Name]

- **Platform**: [PicoCTF / HackTheBox / etc.]
- **Category**: [Web / Pwn / Reverse / Crypto / Forensics / General]
- **Difficulty**: [Easy / Medium / Hard]
- **Points**: [100 pts]
- **Author / Designer**: [Challenge Author]
- **Date Solved**: YYYY-MM-DD

---

## 🎯 Challenge Description

> *Paste the challenge prompt, description, and hint text here.*

---

## 🧰 Tools & Technologies Used

- **Analysis Tools**: [e.g., Ghidra, GDB + GEF, Wireshark, Burp Suite]
- **Libraries / Frameworks**: [e.g., Python 3, `pwntools`, `requests`, `SageMath`]
- **Command Line**: [e.g., `exiftool`, `strings`, `binwalk`, `tshark`]

---

## 🔍 Initial Triage & Reconnaissance

1. **File Identification**:
   ```bash
   file challenge_bin
   checksec --file=challenge_bin
   ```
2. **Key Findings during Recon**:
   - Security mitigations enabled (NX, Canary, PIE, ASLR).
   - Interesting strings or endpoints discovered.

---

## 💡 Vulnerability & Root Cause Analysis

Explain **why** the vulnerability exists in technical terms:
- What line of code or logic leads to the vulnerability?
- What security check was missing or flawed?

---

## 🚀 Step-by-Step Exploitation

### Step 1: Locating the Target Function / Injection Point
Detailed analysis of the code / binary / request.

### Step 2: Crafting the Payload
Show how the payload was constructed (e.g. calculation of offsets, ROP gadget chain, SQL payload).

### Step 3: Triggering the Exploit
Execution steps and observed output.

---

## 🤖 Solution Script (`solve.py`)

```python
#!/usr/bin/env python3
"""
Automated Solve Script for [Challenge Name]
Category: [Category]
Author: [Your Name]
"""

from pwn import *

# Setup target context
context.binary = elf = ELF('./challenge_bin', checksec=False)
context.terminal = ['tmux', 'splitw', '-h']

def main():
    # p = process('./challenge_bin')
    p = remote('saturn.picoctf.net', 12345)

    # Payload construction
    offset = 44
    target_addr = elf.symbols['win']

    payload = flat({
        offset: target_addr
    })

    p.sendlineafter(b'Input: ', payload)
    
    # Receive flag
    flag = p.recvall().decode()
    log.success(f"Flag obtained: {flag}")

if __name__ == '__main__':
    main()
```

---

## 🚩 Flag

```text
picoCTF{example_flag_here_12345}
```

---

## 🎓 Key Takeaways & Remediation

- **What I Learned**: [Key technical takeaway]
- **Remediation / Secure Coding Advice**: How developers/admins should fix this vulnerability (e.g., replace `gets()` with `fgets()`, use parameterized SQL queries, enable ASLR/Stack Canaries).
