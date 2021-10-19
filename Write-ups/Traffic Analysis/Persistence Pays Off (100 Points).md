# Persistence Pays Off
![Category](http://img.shields.io/badge/Category-Traffic_Analysis-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-100-brightgreen?style=for-the-badge)

## Details
>Luciafer might have just bit off more than she can chew! She has encountered an adversary that is counter-attacking her system!
> 
>Luciafer's Lytton Labs adversary executed a command to attain persistence on her computer. This command will allow the adversary to regain a connection to her computer again later, even if she reboots it.
> 
> What is the packet number where this command is executed. For example: `flag{93721}`.
> 
> Use the PCAP file from Monstrum ex Machina.
---

We'll start the point where Luciafer downloaded the `Secret-decoder.bin` file, by filtering for `ftp-data` and locating the packet.

![image](https://user-images.githubusercontent.com/73170900/137892623-838996d1-5188-44d1-8bbd-f48a91ab507a.png)

Then, when we clear the `ftp-data` filter we will still have the same packet selected in the packet capture file.

Now if we start scrolling through the packets below this, we can see what happened after the file was downloaded.

Not too much further down at packet number `160404` we can see some `TCP` packets.

![image](https://user-images.githubusercontent.com/73170900/137893318-69e08c0b-a763-43a9-b0b3-f8dbde61d2ab.png)

If we select the first one and `follow the TCP stream` we see a whole bunch of commands being run;

![image](https://user-images.githubusercontent.com/73170900/137893423-e9db9c1b-eab8-4344-b97e-b044428d3717.png)

In particular we can see the following line where the attacker a cron job is being created to ensure the ll-connect.bin file is launched!

```
sudo /bin/bash -c "echo '*/5 * * * * root /usr/bin/ll-connect.bin' > /etc/cron.d/da-ll-backup-job"
```

Closing the TCP stream, we can see this happening in packet number `160468`

![image](https://user-images.githubusercontent.com/73170900/137893762-9b1fb949-36a3-477a-bfb7-fdd6ad9d8e80.png)

Therfore our flag is;

## flag{160468}

