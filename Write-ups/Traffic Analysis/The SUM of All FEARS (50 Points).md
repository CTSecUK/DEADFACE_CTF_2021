# The SUM of All FEARS
![Category](http://img.shields.io/badge/Category-Traffic_Analysis-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-50-brightgreen?style=for-the-badge)

## Details

>After hacking a victim's computer, Luciafer downloaded several files, including two binaries with identical names, but with the extensions .exe and .bin (a Windows binary and a Linux binary, respectively).
>
>What are the MD5 hashes of the two tool programs? Submit both hashes as the flag, separated by a |: flag{ExeMD5|BinMD5}
>
>Use the PCAP from LYTTON LABS 01 - Monstrum ex Machina.
---

This time we filter the packet capture by `ftp-data`

![image](https://user-images.githubusercontent.com/73170900/137828178-9b6dc235-2b11-4a34-96f2-88c1e8fb54f1.png)

Scrolling through the packets we can see;

![image](https://user-images.githubusercontent.com/73170900/137828269-9a139a2b-8854-4f56-bf1c-eec1edf5194c.png)

First we select one of the packets relating top the file `lytton-crypt.exe` and `Follow TCP Stream`;

![image](https://user-images.githubusercontent.com/73170900/137828321-4c3a4f7a-0b82-4eed-b237-2286e535f425.png)

Then we change the data to be in `RAW` format

![image](https://user-images.githubusercontent.com/73170900/137828505-5cadcf0c-159a-47ab-9bde-9b6fb92e9512.png)

And click the  `Save as...` button saving the file as `lytton-crypt.exe`

We then repeat the process for the `lytton-crypt.bin` file.

Select one of the packets relating top the file `lytton-crypt.bin` and `Follow TCP Stream`;

Then we change the data to be in `RAW` format

And click the  `Save as...` button saving the file as `lytton-crypt.bin`

Now we have both files exported, we can run;

```
❯ md5sum lytton-crypt.*
8a84e7153aa083b66cd89c652bef27da  lytton-crypt.bin
9cb9b11484369b95ce35904c691a5b28  lytton-crypt.exe
```

## flag{9cb9b11484369b95ce35904c691a5b28|8a84e7153aa083b66cd89c652bef27da}
