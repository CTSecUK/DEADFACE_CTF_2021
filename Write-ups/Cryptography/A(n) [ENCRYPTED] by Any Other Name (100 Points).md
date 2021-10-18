# A(n) [ENCRYPTED] by Any Other Name
![Category](http://img.shields.io/badge/Category-Cryptography-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-100-brightgreen?style=for-the-badge)

## Details
>An encrypted message from spookyboi has been intercepted by law enforcement, but it is encrypted with an unknown algorithm and an unknown password. We know that he likes to speak in riddles, so perhaps he gave a riddle to one of his cohorts so they would know how to decrypt the message. Discover the algorithm and password, then decrypt the message below. Enter the flag as flag{this-is-the-flag}.
>
>(Hint: We know that the message is encrypted with Electronic Code Book [ECB] cipher block mode, and we know that the password is in lower case.)
>
> 
[View Message](https://tinyurl.com/4jcbrmud)
---

The encrypted message is as follows;

```
AmYiuw8WHXEpsgNZzGURwW7pXb6APcp7v4HWPzXirriOP3q3fFtCssImT5LR+edaN1k1+lBTbW1rjY/wZSIsPjmY2LOk2FuRBk9i0K25iolP5jtJBt+HyhWZ3EadYNNE24pG6o+znsseud9DIE3zaIObkMFBj6xsWVrhALpju4cJrQpoo74MlJ7cHURHkOC7cKdsMo5kdYA4CpHCEhljvfNSR82nM4Ee9HaVMO58/okaoAtfGadMZcLVadut5sJfVzLzzG0G+QLOAkD/qPtfixggtuDURXkHQ0m2KANEi/3+478bhPoX4AciR5DSRw5zvsuF9JFEu7UCa39KggeAIB0dayX2Ho7hCI2zWTAt+q1WKX8V55toBQd6wtA+fjAsNtLzuzMKhlg6bP7HIzSH8V81C+ocTcTLo5Ijy/ZKaQt7XcDmdRsPVJihQqMu5Pw+5BKbjVNsFL4dcNRfNr4dNQ==
```

The description mentions;
> _"We know that he likes to speak in riddles, so perhaps he gave a riddle to one of his cohorts so they would know how to decrypt the message"_

so we head back to the  [Ghost Town](https://ghosttown.deadface.io/) forum site, where we find the folowing [thread](https://ghosttown.deadface.io/t/hint-for-mort1cia/47) which contains this clue;

![image](https://user-images.githubusercontent.com/73170900/137743217-1361b146-d1bf-47f9-924a-cfd3e46422f2.png)

Now we can use an online tool to decrypte the message - [https://www.tools4noobs.com/online_tools/decrypt/](https://www.tools4noobs.com/online_tools/decrypt/)

The Password/Key is: _**"a synonym of Spook, Spectre, Spirit, Phantasm"**_ - for this I'd guess `ghost`

The Algorithm: _**"a homonym of"**_ - a homonym of ghost could be `Gost` which is one of the algorithm options.

Putting all these pieces tother we get;

![image](https://user-images.githubusercontent.com/73170900/137744645-b57c7ae1-f3a2-484f-8313-9d48c702571e.png)

## flag{the-USSR-is-the-GOST-with-the-MOST}
