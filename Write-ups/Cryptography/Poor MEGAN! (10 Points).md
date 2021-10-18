# Poor MEAGAN!
![Category](http://img.shields.io/badge/Category-Cryptography-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-10-brightgreen?style=for-the-badge)

## Details
![image](https://user-images.githubusercontent.com/73170900/137739909-b98abfbb-dc24-43ef-a82a-0830e6197cda.png)

>Oh, NO! Poor Megan! She's just been bitten by a ZOMBIE! We can save her if we act fast, but the formula for the antidote has been scrambled somehow. Figure out how to unscramble >the formula to save Megan from certain zombification. Enter the answer as flag{here-is-the-answer}.
>
>The formula for the antidote: 
>j2rXjx9dkhW9eLKsnMR9cLDVjh/9dwz1QfGXm+b9=wKslL1Zpb45
---

The string looks like it could be Base64 Encoded but if put the string into [CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true)&input=ajJyWGp4OWRraFc5ZUxLc25NUjljTERWamgvOWR3ejFRZkdYbStiOT13S3NsTDFacGI0NQ) with a Base64 decode recipe you ca seen taht it does not decode.

![image](https://user-images.githubusercontent.com/73170900/137740278-213e6afa-099c-4ea1-b329-d517683b93da.png)

However you'll notice an Alphabet option, which can be used with the base64 decode recipe, which has an option for Megan35 encoding;

![image](https://user-images.githubusercontent.com/73170900/137739682-bb17be2f-037c-4cbd-9f9c-c0f4bc14b6ab.png)

Changing the Alphabet/encoding to this seems allows the base 64 to be decoded! - [Cyberchef](https://gchq.github.io/CyberChef/#recipe=From_Base64('3GHIJKLMNOPQRSTUb%3DcdefghijklmnopWXYZ/12%2B406789VaqrstuvwxyzABCDEF5',true)&input=ajJyWGp4OWRraFc5ZUxLc25NUjljTERWamgvOWR3ejFRZkdYbStiOT13S3NsTDFacGI0NQ)

## flagflag{flag{Six-Parts-Honey-One-Part-Garlic}}
