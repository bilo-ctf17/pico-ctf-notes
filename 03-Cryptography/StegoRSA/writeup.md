# Writeup: StegoRSA

- **Platform**: picoCTF 2026
- **Category**: Cryptography
- **Difficulty**: Easy
- **Author**: Yahaya Meddy

---

## 🎯 Challenge Description

> A message has been encrypted using RSA. The public key is gone... but someone might have been careless with the private key. Can you recover it and decrypt the message?

![Challenge Details](./assets/challenge_details.png)

---

## 🧰 Tools Used

- **ExifTool**: Metadata extraction from image files
- **CyberChef**: Data decoding (`From Hex`) and asymmetric decryption (`RSA Decrypt`)

---

## 🔍 Initial Triage & Reconnaissance

We were provided with two files:
- `image.jpg`: A JPEG image file suspected of containing hidden data.
- `flag.enc`: The RSA-encrypted flag file.

Running `exiftool` on `image.jpg` revealed a long hex string hidden within the image metadata's `Comment` field:

```bash
──(kali㉿kali)-[~/pico-ctf-notes/03-Cryptography/StegoRSA]
└─$ exiftool image.jpg
ExifTool Version Number         : 13.50
File Name                       : image.jpg
Directory                       : .
File Size                       : 21 kB
File Modification Date/Time     : 2026:08:03 04:17:21-04:00
File Access Date/Time           : 2026:08:03 04:18:16-04:00
File Inode Change Date/Time     : 2026:08:03 04:17:21-04:00
File Permissions                : -rw-rw-rw-
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Comment                         : 2d2d2d2d2d424547494e2050524956415445204b45592d2d2d2d2d0a4d494945765149424144414e42676b71686b6947397730424151454641415343424b63776767536a41674541416f494241514471336d546873754d466f47332f0a776d6c79743466555a3932734938664d4c494d4655565776785836574d50484131564a6c6f386b667835736b69487a57576c35585949616c4772374b573758300a6b7a4e6e6e566746336b556567525a4d5338487a54517435643148525742515443456b74665561654f2b724c35624a4c7050367552526762326567794e3963710a4b326a6f7a4651583864496c4d746j41544734795744436j484746796358764b357236664f784137445058386j6938474870657859716j2b724e394845446f590a473742574c69574c307a64665a42577a4a4878635873477475446j2b58486e6871307633522f6d4a556f50654e446j6a5164444b516b4634344a6c4d7a4f2f0a7646353636614d36575754332b36426b366e327861695a4d71624f4447653449614c7a48546d52326532735636714d5a69527349784c364536575178574f774d0a4c37715a4f2b677841674d4241414543676745414a515546794b537a62344a7765585452614846626846515577572b39713858447077735775456238546847320a692b727a3046664844706b64326f6831694e636a52306l334835536f79443435587179664178747573596f59624a6564323076413753656e31393774546635720a4e356c735067664c64754273674b6c4654504b773654344a7855594d2b52774b6344663576574532494c5335306637594e75336678716c574e2b49657a556e300a4e4f4c4230746d457a417031744a65634a4a32324d384f356b4b586e4b377546714261666b42566j6a66614938654531464931687a7544414744452f446c490a3042666d57376762344b4463337672684e7631324d5a446543633570586b58506e716d4271726j73444f766c6864316d6b7258397834396e764b2f354f55554e0a43656779637365534e506944506965394b6c4c424d39716879577767686d66714a614c445869515477774b426751447475653141553435564d654d304f6e53660a6f7343594f6f47504f6a6155436b6a7773474b34416j74504749514b4f696j4b36426b6d4379624951702f71797533634b374b4b695041684f504877434f624c0a31745561592b4b6b734d704952706b464d4f4a7865686j59686250457a7367705775394a616e6d537354484e30723676756c4f554c57534c4f4967585038414e0a546d5350457a5054353432575749742b4439756752655a4c6j774b4267514438374477385a5750385a7775724f4b58574338533536724373386j514a75734f6b0a62746c4f7645304f4a7969504954417935584e35456f3370386l59706f6e626b4INIXCAUldtt6TUDD9AC8VFpbN2Fa8y0aL2kP1nOhph8emGCrg2shgMYK1HRvGjEhT3gA3wX7NriO/QvqwDYkR1HWT/Cf9Pxj0aHxJiKhOwPwKBgQCo3yntRy3V0VF/+YJ9ICVGPlFoyEabFU9JQ1NtOZCeGGE7zqLJuOSchNFw8vsc1Djx7UywYqKRSSAiiJBbQQG8iu/KCMaAqSS7m39hGl/7kKMrQO9dO6ErZFdJmiluG5i8K6MlU5WI7txIIUyLpz6kf6AKn4G7jFxRJyUlvMIewKBgB9TTv6X/DNFu/8/6+I/4OS5+ZniAan21MZn6EhFMDIBjZd0n9id7JhhQOxp1EbEY11g3ZNswddS23s+VI7i2W6gRpWiuUB13RYVIykQAZBS1+XdL5PumfUzUtQCjk04bD9Y7V8GQGJl26PyGWjA17PUlYE6s23MVPod3hQEbB3XAoGAGmQWjQ2MOlpAjlZfyfyTh4otp2T2KxZim/NcxfL1NUK+VxSLCQtxdnVIWcg0vmNLSB+9eF1dawts3BF3uRxQeswBhJCl0kyIxDFXZPz8u7sRROrRK11YyUznG0OTfnb9Vjl8TbhpZVH-Oyp754MUwkkM+srAQK+sVVR0Qbl0yU=0a2d2d2d2d2d454e442050524956415445204b45592d2d2d2d2d0a
Image Width                     : 512
Image Height                    : 512
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 512x512
Megapixels                      : 0.262
```

---

## 🚀 Step-by-Step Solution

### Step 1: Recovering the RSA Private Key via CyberChef

1. Copy the hex-encoded `Comment` data extracted by `exiftool`.
2. Paste the data into **CyberChef** as the Input.
3. Add the **`From Hex`** recipe with `Delimiter: Auto`.
4. CyberChef decodes the hex content into the full PEM RSA Private Key:

![CyberChef From Hex](./assets/cyberchef_from_hex.png)

```pem
-----BEGIN PRIVATE KEY-----
MIIEvIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQDq3mThsuMFoG3/
...
-----END PRIVATE KEY-----
```

---

### Step 2: Decrypting `flag.enc`

1. In **CyberChef**, add the **`RSA Decrypt`** recipe.
2. Configure the **`RSA Decrypt`** recipe settings:
   - **RSA Private Key (PEM)**: The extracted PEM private key.
   - **Encryption Scheme**: `RSAES-PKCS1-V1_5`
3. Load `flag.enc` as the Input to the `RSA Decrypt` operation.
4. CyberChef successfully decrypts `flag.enc` to obtain the flag:

![CyberChef RSA Decrypt](./assets/cyberchef_rsa_decrypt.png)

---

## 🚩 Flag

```text
picoCTF{rs4_k3y_1n_1mg_d8526dc3}
```

---

## 🎓 Key Takeaways

- **Metadata Steganography**: Sensitive data such as private keys can easily be embedded in image metadata (EXIF / JPEG Comments).
- **Steg-Crypto Combination**: Always check for embedded structural keys inside stego artifacts when attempting to solve CTF crypto challenges with missing keys.
