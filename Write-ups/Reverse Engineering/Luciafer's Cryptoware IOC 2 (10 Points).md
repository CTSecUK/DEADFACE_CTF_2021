# Luciafer's Cryptoware IOC 2

![Category](http://img.shields.io/badge/Category-Reverse_Engineering-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-10-brightgreen?style=for-the-badge)

## Details

>Luciafer's cryptoware causes even more ruckus by encrypting the victim's file names. Decrypt the filename and enter it as the flag: Example flag{important-document.ext}.
>
> [Encrypted File](https://tinyurl.com/33e6t3xs)

---

Downloading the file we see it has a name of `fkduohv-d-jhvfklfnwhu-wr-gdun-dqjho-01.oodev`

if we enter the file name into [CyberChef](https://gchq.github.io/CyberChef/#recipe=ROT13(true,true,false,23)&input=ZmtkdW9odi1kLWpodmZrbGZud2h1LXdyLWdkdW4tZHFqaG8tMDEub29kZXY) and apply a `ROT13` recipe, we can alter the rotation until we find;

![image](https://user-images.githubusercontent.com/73170900/137824700-0d249115-73d5-48aa-a682-1d261d10f34a.png)

## flag{charles-a-geschickter-to-dark-angel-01.llabs}
