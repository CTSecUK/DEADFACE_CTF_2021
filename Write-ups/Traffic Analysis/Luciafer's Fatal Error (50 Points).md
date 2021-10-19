# Luciafer's Fatal Error
![Category](http://img.shields.io/badge/Category-Traffic_Analysis-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-50-brightgreen?style=for-the-badge)

## Details
>Luciafer, consummate hacker, got cocky and careless. She made a fatal mistake, and in doing so, gave control of her computer to... someone. She ran a program on her computer that she shouldn't have.
> 
> What is the md5sum of the program? Submit the flag as: `flag{MD5}`.
> 
> Use the PCAP from Monstrum ex Machina
---

![image](https://user-images.githubusercontent.com/73170900/137882090-6174c979-b403-4dfd-ae6d-b5d91dfe3d7e.png)

Removing the `FTP` filter and looking at the packets which follow, we can ssee the folloowing in the `TCP stream`

![image](https://user-images.githubusercontent.com/73170900/137883166-8653fa0a-246f-44ca-9dbb-0bb46243317a.png)

This appears to be launching a shell.

As before if we then re-filter by `ftp-data`, select the packet relating to `secret-decoder.bin` and extract and save it from the `TCP Stream`.

![image](https://user-images.githubusercontent.com/73170900/137882197-02795c0a-5151-47ce-8ce4-6602ebf0bf24.png)

Now that we have a copy of the file on our local machine we can run;

```bash
❯ md5sum secret-decoder.bin
42e419a6391ca79dc44d7dcef1efc83b  secret-decoder.bin
```

## flag{42e419a6391ca79dc44d7dcef1efc83b}

