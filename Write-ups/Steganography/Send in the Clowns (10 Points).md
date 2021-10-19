# Send in the Clowns
![Category](http://img.shields.io/badge/Category-Steganography-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-10-brightgreen?style=for-the-badge)

## Details

> There is a secret hidden somewhere in this image. Can you find it? Submit the flag as flag{this-is-the-flag}.
> 
> [Link to Image](https://tinyurl.com/y9xjz7b4)
> SHA1: 74eaae618bf508ef2715533bfdff3153dd996e89
---

![image](https://user-images.githubusercontent.com/73170900/137825074-87f2d016-0ba4-4764-8526-bf297b3b8e89.png)

If we run the strings command against the file...

```bash
❯ strings -n 12 steg02.jpg
```

We see the flag;

```
❯ strings -n 12 steg02.jpg
http://ns.adobe.com/xap/1.0/
<?xpacket begin='
' id='W5M0MpCehiHzreSzNTczkc9d'?>
<x:xmpmeta xmlns:x='adobe:ns:meta/' x:xmptk='Image::ExifTool 12.16'>
<rdf:RDF xmlns:rdf='http://www.w3.org/1999/02/22-rdf-syntax-ns#'>
 <rdf:Description rdf:about=''
  xmlns:prism='http://prismstandard.org/namespaces/basic/2.0/'>
  <prism:wordCount>1</prism:wordCount>
 </rdf:Description>
</x:xmpmeta>
<?xpacket end='w'?>
flag{s3nd_in_the_kl0wns}
❯ strings -n 12 steg02.jpg
```

## flag{s3nd_in_the_kl0wns}
