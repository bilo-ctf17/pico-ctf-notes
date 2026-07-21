# ↩️ Undo (picoCTF)
- **Category:** General Skills
- **Points:** 100
- **Difficulty:** Easy
- **Format:** Interactive CLI Challenge

---

## 📖 Challenge Overview
The **Undo** (or *Text Transformations*) challenge requires reversing a series of common text encodings and transformations applied to the flag in reverse order. By connecting to a remote server using netcat, the user is presented with a transformed string and a hint at each step, and must input the correct Linux CLI command to undo the transformation.

---

## 🧠 My Learning Journey & Discovery

### Phase 1: CyberChef Exploration 🧪
I started by inspecting the initial encoded string: `KTBxcDI0bnIwLWZhMDFnQHplMHNmYTRlRy1nazNnLXRhMWZlcmlyRShTR1BicHZj`

* **Observation:** The string ends without typical base64 padding (`=`), but has base64-like characters.
* **Action:** I put it into **CyberChef** and applied the **From Base64** recipe.
* **Discovery:** The output was `)0qp24nr0-fa01g@ze0sfa4eG-gk3g-ta1ferirE(SGPbpvc`. I noticed that:
  - The text was clearly reversed (e.g. starting with `)` and ending with `(`).
  - The suffix `(SGPbpvc` reversed is `cvpbPGS(`, which looked like a ROT13-encoded version of `picoCTF(`.
  - This confirmed the challenge has a series of reversible, nested transformations.

```text
🧪 CyberChef Recipe Diagram
┌────────────────────────────────────────────────────────────────────────┐
│ Input:                                                                 │
│ KTBxcDI0bnIwLWZhMDFnQHplMHNmYTRlRy1nazNnLXRhMWZlcmlyRShTR1BicHZj       │
├────────────────────────────────────────────────────────────────────────┤
│ Recipe: From Base64 (Remove non-alphabet chars = True)                  │
├────────────────────────────────────────────────────────────────────────┤
│ Output:                                                                │
│ )0qp24nr0-fa01g@ze0sfa4eG-gk3g-ta1ferirE(SGPbpvc                       │
└────────────────────────────────────────────────────────────────────────┘
```

---

### Phase 2: Shell Interaction & `rev` Command 🐚
Now that I knew the decoded text was reversed, I connected to the challenge server via netcat. 
1. **Step 1:** The server asked to reverse the Base64 encoding. I input `base64 -d`, which was correct.
2. **Step 2:** The current flag became the reversed string: `)0qp24nr0-fa01g@ze0sfa4eG-gk3g-ta1ferirE(SGPbpvc`.
3. **Research:** I searched how to reverse a string in Linux and found the command **`rev`**. 
4. **Result:** Entering `rev` succeeded and gave: `cvpbPGS(Eriref1at-g3kg-Ge4afs0ez@g10af-0rn42pq0)`.

---

### Phase 3: Mastering the `tr` (Translate) Utility 📖
For the subsequent steps, I had to swap specific characters. I looked up the Linux manual page (`man tr`) to understand how to translate ranges and specific sets of characters.

#### Key Takeaways from the `tr` Man Page:
* **Synopsis:** `tr [OPTION]... STRING1 [STRING2]`
* **How it works:** It translates characters in `STRING1` to the corresponding characters in `STRING2` based on their index:
  - For swapping dashes and underscores: `tr '-' '_'` replaces all `-` with `_`.
  - For replacing parentheses with curly braces: `tr '()' '{}'` maps `(` to `{` and `)` to `}`.
  - For ROT13 decoding: `tr 'A-Za-z' 'n-za-mN-ZA-M'` (or `tr 'A-Za-z' 'N-ZA-Mn-za-m'`) shifts alphabet ranges by 13 characters while mapping case.

Armed with this understanding of the `tr` logic, I solved the remaining steps and successfully retrieved the flag!

---

## 🛠️ Step-by-Step Resolution Table

| Step | Current Flag / Input | Hint / Applied Transformation | Correct Command | Reversal Explanation |
|:---:|:---|:---|:---:|:---|
| **1** | `KTBxcDI0bnIwLWZhMDFnQHplMHNmYTRlRy1nazNnLXRhMWZlcmlyRShTR1BicHZj` | Base64 encoded. | `base64 -d` | Decodes the Base64 representation to recover the raw ASCII characters. |
| **2** | `)0qp24nr0-fa01g@ze0sfa4eG-gk3g-ta1ferirE(SGPbpvc` | Reversed the text. | `rev` | Reverses the string character-by-character from end to start. |
| **3** | `cvpbPGS(Eriref1at-g3kg-Ge4afs0ez@g10af-0rn42pq0)` | Replaced underscores (`_`) with dashes (`-`). | `tr '-' '_'` | Swaps all occurrences of `-` back to `_`. |
| **4** | `cvpbPGS(Eriref1at_g3kg_Ge4afs0ez@g10af_0rn42pq0)` | Replaced curly braces (`{}`) with parentheses (`()`). | `tr '()' '{}'` | Translates `(` to `{` and `)` to `}` to restore the standard flag format. |
| **5** | `cvpbPGS{Eriref1at_g3kg_Ge4afs0ez@g10af_0rn42pq0}` | Applied ROT13 to letters. | `tr 'A-Za-z' 'n-za-mN-ZA-M'` | Shifts alphabet letters by 13 positions to decode ROT13. |

---

## 📊 Visualizing the Pipeline

```mermaid
graph TD
    Start["KTBxcDI0bnIwLWZhMDFnQHplMHNmYTRlRy1nazNnLXRhMWZlcmlyRShTR1BicHZj"]
    
    Start -->|1. base64 -d| Step2[")0qp24nr0-fa01g@ze0sfa4eG-gk3g-ta1ferirE(SGPbpvc"]
    Step2 -->|2. rev| Step3["cvpbPGS(Eriref1at-g3kg-Ge4afs0ez@g10af-0rn42pq0)"]
    Step3 -->|3. tr '-' '_'| Step4["cvpbPGS(Eriref1at_g3kg_Ge4afs0ez@g10af_0rn42pq0)"]
    Step4 -->|4. tr '()' '{}'| Step5["cvpbPGS{Eriref1at_g3kg_Ge4afs0ez@g10af_0rn42pq0}"]
    Step5 -->|5. ROT13 Reversal| Final["picoCTF{Revers1ng_t3xt_Tr4nsf0rm@t10ns_0ea42cd0}"]

    style Start fill:#2a2f35,stroke:#ff6b6b,stroke-width:2px,color:#fff
    style Final fill:#1e3d2f,stroke:#4caf50,stroke-width:2px,color:#fff
    style Step2 fill:#2b2d42,stroke:#d90429,stroke-width:1px,color:#fff
    style Step3 fill:#2b2d42,stroke:#d90429,stroke-width:1px,color:#fff
    style Step4 fill:#2b2d42,stroke:#d90429,stroke-width:1px,color:#fff
    style Step5 fill:#2b2d42,stroke:#d90429,stroke-width:1px,color:#fff
```

---

## 💻 Terminal Log

```bash
┌──(kali㉿kali)-[~/pico-ctf-notes/01-General-Skills]
└─$ nc foggy-cliff.picoctf.net 56138                                                                                         
===Welcome to the Text Transformations Challenge!===

Your goal: step by step, recover the original flag.
At each step, you'll see the transformed flag and a hint.
Enter the correct Linux command to reverse the last transformation.

--- Step 1 ---
Current flag: KTBxcDI0bnIwLWZhMDFnQHplMHNmYTRlRy1nazNnLXRhMWZlcmlyRShTR1BicHZj
Hint: Base64 encoded the string.
Enter the Linux command to reverse it: base64 -d
Correct!

--- Step 2 ---
Current flag: )0qp24nr0-fa01g@ze0sfa4eG-gk3g-ta1ferirE(SGPbpvc
Hint: Reversed the text.
Enter the Linux command to reverse it: rev
Correct!

--- Step 3 ---
Current flag: cvpbPGS(Eriref1at-g3kg-Ge4afs0ez@g10af-0rn42pq0)
Hint: Replaced underscores with dashes.
Enter the Linux command to reverse it: '-' '_'
Incorrect. Try again.
Output: [Error] Command not allowed.
Hint: Try reversing: tr '_' '-'

Enter the Linux command to reverse it: tr '-' '_'
Correct!

--- Step 4 ---
Current flag: cvpbPGS(Eriref1at_g3kg_Ge4afs0ez@g10af_0rn42pq0)
Hint: Replaced curly braces with parentheses.
Enter the Linux command to reverse it: tr '()' '{}'
Correct!

--- Step 5 ---
Current flag: cvpbPGS{Eriref1at_g3kg_Ge4afs0ez@g10af_0rn42pq0}
Hint: Applied ROT13 to letters.
Enter the Linux command to reverse it: tr 'A-Za-z' 'n-za-mN-ZA-M'
Correct!

Congratulations! You've recovered the original flag:
>>> picoCTF{Revers1ng_t3xt_Tr4nsf0rm@t10ns_0ea42cd0}
```
