# Blood Bash
![Category](http://img.shields.io/badge/Category-Forensics-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-10-brightgreen?style=for-the-badge)

## Details

>We've obtained access to a system maintained by bl0ody_mary. There are five flag files that we need you to read and submit. Submit the contents of flag1.txt.
>
> Username: `bl0ody_mary`
> Password: `d34df4c3`
>
> `bloodbash.deadface.io:22`
---

First we connect to shell using the suplied credentials.
```
❯ ssh bl0ody_mary@bloodbash.deadface.io
bl0ody_mary@bloodbash.deadface.io's password: 
bl0ody_mary@16ef1481fce1:~$ 
```

Next we run: `ls -R` and see the follwiwng;

```
bl0ody_mary@16ef1481fce1:~$ ls -R
.:
'De Monne Customer Portal.pdf'   Documents   Downloads   Music   Pictures   Videos

./Documents:
flag1.txt

./Downloads:

./Music:

./Pictures:

./Videos:
```


so we try reading the flag using: `cat Documents/flag1.txt`

```
flag{cd134eb8fbd794d4065dcd7cfa7efa6f3ff111fe}
```

## flag{cd134eb8fbd794d4065dcd7cfa7efa6f3ff111fe}

