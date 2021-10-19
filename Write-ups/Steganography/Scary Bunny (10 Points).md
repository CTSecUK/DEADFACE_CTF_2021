# Scary Bunny
![Category](http://img.shields.io/badge/Category-Steganography-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-10-brightgreen?style=for-the-badge)

## Details

> What could be inside this creepy rabbit?
> 
> [Download image](https://tinyurl.com/4csyne6s)
> 
> SHA1: 7ab2d9b1986ae12b780d0a2124a3adce6ed4c4e1
---

![image](https://user-images.githubusercontent.com/73170900/137825375-e75747fb-09a6-4ac8-b1b7-51b38d2c5018.png)

If we run `steghide` agains the image using a `blank` password...

```bash
❯ steghide extract -sf  bunny.jpg
Enter passphrase: 
wrote extracted data to "steganopayload730241.txt".
```

We can see that it ecxtracts some information!

```bash
❯ cat steganopayload730241.txt
flag{Carr0t}
```

## flag{Carr0t}
