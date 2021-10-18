# Blood Bash 4
![Category](http://img.shields.io/badge/Category-Forensics-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-200-brightgreen?style=for-the-badge)

## Details

>A sensitive file from De Monne was exfiltrated by mort1cia. It contains data relating to a new web portal they're creating for their consumers. Read the contents of the file and return the flag as `flag{flag_goes_here}`.
>
> Username: `bl0ody_mary`
> Password: `d34df4c3`
>
> `bloodbash.deadface.io:22`
---

Connect to shell...

Run: `la -al`

```
-output from ls command-
```

note `.pdf`

Then: `base64 dsadsa.pdf`

Copy Base64 encoded string from shell

On you local machine past the b64 string into a file and save as `encoded`

Then run `base64 -d encoded > file.pdf`

Open the resulting pdf file in your favourite PDF viewer to see the flag;

## flag{_____}
