# Windows Pains 4
![Category](http://img.shields.io/badge/Category-Forensics-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-200-brightgreen?style=for-the-badge)

## Details

> We want to see if any other machines are infected with this malware. Using the [memory dump file](https://tinyurl.com/wcekj3rt) from Window Pains, submit the SHA1 checksum of the malicious process.
>
> Submit the flag as `flag{SHA1 hash}`.
>
> **CAUTION:** Practice good cyber hygiene! Use an isolated VM to download/run the malicious process. While the malicious process is relatively benign, if you're using an insecurely-configured Windows host, it may be possible for someone to compromise your machine if they can reach you on the same network.
---


Using Volatility3 we run `sudo python3 vol.py -f physmemraw windows.dumpfiles --pid 8081`

```
-output here-
```

Next; `sha1sum file...........userinit.exe`

```
-output here-
```


## flag{__________________________________}
