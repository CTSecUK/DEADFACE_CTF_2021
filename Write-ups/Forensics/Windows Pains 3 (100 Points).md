# Windows Pains 3
![Category](http://img.shields.io/badge/Category-Forensics-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-100-brightgreen?style=for-the-badge)

## Details

One of De Monne's employees had their personal Windows computer hacked by a member of DEADFACE. The attacker managed to exploit a portion of a database backup that contains sensitive employee and customer PII.

> Using the [memory dump file](https://tinyurl.com/wcekj3rt) from Window Pains, find out the name of the malicious process.
>
> Submit the flag as `flag{process-name_pid}` (include the extension)..
>
> Example: `flag{svchost.exe_1234}`
---


Using Volatility3 we run `sudo python3 vol.py -f physmemraw windows.pstree`

```
-output here-
```

Next; `sudo python3 vol.py -f physmemraw windows.cmdLine`

```
-output here-
```

Next; `sudo python3 vol.py -f physmemraw windows.pslist.PsList --pid 8081`

```
-output here-
```

## flag{userinit.exe_8081}
