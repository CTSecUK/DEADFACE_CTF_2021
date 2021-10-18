# Blood Bash 3
![Category](http://img.shields.io/badge/Category-Forensics-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-100-brightgreen?style=for-the-badge)

## Details

>There's a flag on this system that we're having difficulty with. Unlike the previous flags, we can't seem to find a file with this flag in it. Perhaps the flag isn't stored in a traditional file?
>
> Username: `bl0ody_mary`
> Password: `d34df4c3`
>
> `bloodbash.deadface.io:22`
---

Connect to shell...

Run: `netsat -alnp"`

```
-output from nestat command-
```

Note the following line: `cat Documents/.demone-info.txt`

also note UDP!

connect via netacat to that port like so.. `nc -u 127.0.0.1 12345`

```
-output from nestat command-
```

## flag{_____}

another unintended way to find teh flag was as folllows...

Run: `sudo -l"`

`cat /usr/bin/srv`

```
-Access denied message-
```

`cat /opt/startup.sh`

```
-output from cat startup command-
```

Notice the script executes `/bin/bash` - as root!

`sudo /opt/startup.sh` gives us a root shell

then `cat  /usr/bin/srv`

```
-contaents of /usr/bin/srv-
```

Again we can see the flag here!
