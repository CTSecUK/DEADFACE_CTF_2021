He Thrusts His Fists Against the Post
![Category](http://img.shields.io/badge/Category-Cryptography-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-100-brightgreen?style=for-the-badge)

## Details

![image](https://user-images.githubusercontent.com/73170900/137745677-58c19926-95be-417a-95c0-bb690bb15c72.png)

> {ea-vetgaytereoreh-na}fan--wshbestpasslds-s-hm
---

Looking at the string in the description, it looks like it has standard alphabet characters and even the {} curly braces for the flag, but they aren't in the right place.

This makes me thing the string has been encoded using a transposition cipher.?!

The name of the challenge along with the picture in the challenge details further points me towards a **"Rail Fence Cipher"** (a type of transposition cipher).

Using our old friend [CyberChef](https://gchq.github.io/CyberChef/#recipe=Rail_Fence_Cipher_Decode(4,74)&input=e2VhLXZldGdheXRlcmVvcmVoLW5hfWZhbi0td3NoYmVzdHBhc3NsZHMtcy1obQ) and with a bit of expirementation to find the correct Key and Offset, we find our flag;

![image](https://user-images.githubusercontent.com/73170900/137747012-4017ccea-1498-4bdc-a6e3-6a20dbd0ad75.png)

## flag{and-yet-swears-he-observes-the-phantasms}
