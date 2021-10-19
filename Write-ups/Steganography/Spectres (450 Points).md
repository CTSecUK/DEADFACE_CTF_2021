# Spectres
![Category](http://img.shields.io/badge/Category-Steganography-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-450-brightgreen?style=for-the-badge)

## Details

> We intercepted this image from a suspected insider threat at De Monne Financial. It looks like parts of the image were cut out, but based on conversations between DEADFACE and the insider, we believe DEADFACE's wallet address is hidden in this image.
> 
> [Download image](https://tinyurl.com/yp5ttjzt)
> 
> SHA1: e972d295c2624d3e33ab23c48587b916d6693320
---

![image](https://user-images.githubusercontent.com/73170900/137826979-3d43b912-3365-47ec-b02c-398a0186c873.png)

Apprently the challenge author had intended this challenge to be much harder, requiring a custom script/program to analyse the image pixel bv pixel, but actually this was easily solved using `stesolve`.

Viewing the `Gray Bits` layer we can clearley see the flag;

![image](https://user-images.githubusercontent.com/73170900/137827168-6da59ec9-4c3a-452b-a008-d59bac25a459.png)

## flag{I_s33_d34d_ppl}
