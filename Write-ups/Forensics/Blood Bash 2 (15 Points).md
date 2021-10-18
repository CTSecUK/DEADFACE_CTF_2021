# Blood Bash 2
![Category](http://img.shields.io/badge/Category-Forensics-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-15-brightgreen?style=for-the-badge)

## Details

>We've obtained access to a system maintained by bl0ody_mary. We believe bl0ody_mary stole a sensitive document and is storing it on her Linux machine. Search her system for any files relating to De Monne Financial.
>
> Username: `bl0ody_mary`
> Password: `d34df4c3`
>
> `bloodbash.deadface.io:22`
---

We connect to shell again, but this time we run the command `ls -alR` which results in;

```bl0ody_mary@16ef1481fce1:~$ ls -alR 
.:
total 68
drwxr-xr-x 1 bl0ody_mary bl0ody_mary  4096 Sep 16 12:51  .
drwxr-xr-x 1 root        root         4096 Sep 14 19:15  ..
-rw------- 1 bl0ody_mary bl0ody_mary     1 Sep 16 14:44  .bash_history
-rw-r--r-- 1 bl0ody_mary bl0ody_mary   220 Sep 14 19:15  .bash_logout
-rw-r--r-- 1 bl0ody_mary bl0ody_mary  3771 Sep 14 19:15  .bashrc
-rw-r--r-- 1 bl0ody_mary bl0ody_mary   807 Sep 14 19:15  .profile
-rw-r--r-- 1 bl0ody_mary bl0ody_mary 12444 Sep 14 20:20 'De Monne Customer Portal.pdf'
drwxr-xr-x 2 bl0ody_mary bl0ody_mary  4096 Sep 14 19:16  Documents
drwxr-xr-x 2 bl0ody_mary bl0ody_mary  4096 Sep 14 19:15  Downloads
drwxr-xr-x 2 bl0ody_mary bl0ody_mary  4096 Sep 14 19:15  Music
drwxr-xr-x 2 bl0ody_mary bl0ody_mary  4096 Sep 14 19:15  Pictures
drwxr-xr-x 2 bl0ody_mary bl0ody_mary  4096 Sep 14 19:15  Videos

./Documents:
total 20
drwxr-xr-x 2 bl0ody_mary bl0ody_mary 4096 Sep 14 19:16 .
drwxr-xr-x 1 bl0ody_mary bl0ody_mary 4096 Sep 16 12:51 ..
-rw-r--r-- 1 bl0ody_mary bl0ody_mary   47 Sep 14 19:16 .demonne_info.txt
-rw-r--r-- 1 bl0ody_mary bl0ody_mary   47 Sep 14 19:16 flag1.txt

./Downloads:
total 12
drwxr-xr-x 2 bl0ody_mary bl0ody_mary 4096 Sep 14 19:15 .
drwxr-xr-x 1 bl0ody_mary bl0ody_mary 4096 Sep 16 12:51 ..

./Music:
total 12
drwxr-xr-x 2 bl0ody_mary bl0ody_mary 4096 Sep 14 19:15 .
drwxr-xr-x 1 bl0ody_mary bl0ody_mary 4096 Sep 16 12:51 ..

./Pictures:
total 12
drwxr-xr-x 2 bl0ody_mary bl0ody_mary 4096 Sep 14 19:15 .
drwxr-xr-x 1 bl0ody_mary bl0ody_mary 4096 Sep 16 12:51 ..

./Videos:
total 12
drwxr-xr-x 2 bl0ody_mary bl0ody_mary 4096 Sep 14 19:15 .
drwxr-xr-x 1 bl0ody_mary bl0ody_mary 4096 Sep 16 12:51 ..

```

Here we can see a hiden file called `.demonne_info.txt`

So we try readin the hidden file using `cat Documents/.demonne_info.txt`

```
bl0ody_mary@16ef1481fce1:~$ cat Documents/.demonne_info.txt
flag{a856b162978fe563537c6890cb184c48fc2a018a}
```

## flag{a856b162978fe563537c6890cb184c48fc2a018a}
