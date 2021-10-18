# Windows Pains 2
![Category](http://img.shields.io/badge/Category-Forensics-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-50-brightgreen?style=for-the-badge)

## Details

One of De Monne's employees had their personal Windows computer hacked by a member of DEADFACE. The attacker managed to exploit a portion of a database backup that contains sensitive employee and customer PII.

> Using the [memory dump file](https://tinyurl.com/wcekj3rt) from Window Pains, submit the victim's computer name.
>
> Submit the flag as `flag{COMPUTER-NAME}`.
---


Using Volatility3  we run `sudo python3 vol.py -f physmemraw windows.envars`

```
-output here-
```

Notice near the bottom of the output we see  `DESKTOP-HJKHJSA`


## flag{_____}
