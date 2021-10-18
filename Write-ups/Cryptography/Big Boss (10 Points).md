# Big Boss
![Category](http://img.shields.io/badge/Category-Cryptography-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-10-brightgreen?style=for-the-badge)

## Details

>An anonymous tipster sent us this photo alleging that it's a note written by b3li3f1203. The tipster claims that the note was intended for someone who works at De Monne Financial. They also said it's likely that it has something to do with a phishing campaign. Provide the name of the target individual as the flag in this format: flag{FirstName_LastName}.
>
>[Download Image](https://tinyurl.com/4stj3n4t)

---

Looking at the image we can see it constains some sort of hand written cipher.

![image](https://user-images.githubusercontent.com/73170900/137735468-e0e9422e-417f-4917-aa48-32c8f7d3bbe2.png)

If we enter the string into [CyberChef](https://gchq.github.io/CyberChef/#recipe=ROT13(true,true,false,-14)&input=SHZzIGJzbGggYXNzaHdidSBrd3p6IHBzIGhjcm9tIG9oIGJjY2IuIEJzc3IgaGMgdHdiciBjaWgKWHdhYXdzJ2cga2NmeSBncXZzcml6cyBnYyBrcyB5YmNrIGt2c2Igd2cgcHNnaCBoYyBkdndndgp2d2EuIEh2cyBxb2Fkb3d1YiBic3NyZyBoYyB6Y2N5IHp3eXMgd2ggcW9hcyB0ZmNhCnZ3ZyBwY2dnLCBBb2ZxaWcgUG1ic2YuIFZzIGtjZnlnIG9nIG9iIE9yam9icXNyCkdjemlod2NiZyBHaWRzZmp3Z2NmIC1yY2InaCB0Y2Z1c2hoYyB3YnF6aXJzCmh2b2ggd2IgaHZzIHNhb3d6Lg) and apply a Rot 13 recipe, we can change teh value until we get something readable - in this case -13 (or 38).

>The next meeting will be today at noon. Need to find out
>Jimmie's work schedule so we know when is best to phish
>him. The campaign needs to look like it came from
>his boss, **Marcus Byner**. He works as an Advanced
>Solutions Supervisor -don't forgetto include
>that in the email.

The challange details said teh flag format is the name of the Supervisor which is highlighted above. Therefore the flag is;

## flag{Marcus_Byner}
