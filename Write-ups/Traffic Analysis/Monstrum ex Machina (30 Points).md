# Monstrum ex Machina
![Category](http://img.shields.io/badge/Category-Traffic_Analysis-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-30-brightgreen?style=for-the-badge)

## Details

> Our person on the "inside" of Ghost Town was able to plant a packet sniffing device on Luciafer's computer. Based on our initial analysis, we know that she was attempting to hack a computer in Lytton Labs, and we have some idea of what she was doing, but we need a more in-depth analysis. This is where YOU come in.
> 
> We need YOU to help us analyze the packet capture. Look for relevant data to the potential attempted hack.
> 
> To gather some information on the victim, investigate the victim's computer activity. The "victim" was using a search engine to look up a name. Provide the name with standard capitalization: `flag{Jerry Seinfeld}`.
> 
> [Download file](https://tinyurl.com/35a45kc3)
> 
> SHA1: 6c0caf366dae3e03bcbd7338de0030812536894c
---

We open the packet Capture in wireshark and filetr by `HTTP` traffic

![image](https://user-images.githubusercontent.com/73170900/137827880-bf2cba4b-d515-4b2a-82b2-d376a2727238.png)

Scrolling down through the packets we wsee the following;

![image](https://user-images.githubusercontent.com/73170900/137827708-f7015399-4bde-4588-9db2-1e3b645c6692.png)

If we `Follow the HTTP Stream` for this packet we can see;

![image](https://user-images.githubusercontent.com/73170900/137827784-86b1adbe-792f-4f2e-a58d-d664c27fa9e1.png)

Therefore the flag is;

## flag{Charles Geschickter}
