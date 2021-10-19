# Scanners
![Category](http://img.shields.io/badge/Category-Traffic_Analysis-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-100-brightgreen?style=for-the-badge)

## Details
>Luciafer started the hack of the Lytton Labs victim by performing a port scan.
>
>Which TCP ports are open on the victim's machine? Enter the flag as the open ports, separated by commas, no spaces, in numerical order. Disregard port numbers >= 16384.
> 
> Example: `flag{80,110,111,143,443,2049}`
> 
> Use the PCAP from LYTTON LABS 01 - Monstrum ex Machina.
---

Victim's PC is `192.168.100.103`

Luciafer's PC `192.168.100.106`

We can use the following filter to find traffic `(ip.src == 192.168.100.103) && (ip.dst == 192.168.100.106)`

![image](https://user-images.githubusercontent.com/73170900/137885754-6877e360-d55c-4fb6-917d-39af7588bd7c.png)

Scrolling through the data we see;

![image](https://user-images.githubusercontent.com/73170900/137885534-8ddd29f2-3350-4bdb-9ff0-a0e1b3dee0e0.png)

taking a closer look at one of the open port responses we can see;

![image](https://user-images.githubusercontent.com/73170900/137886001-a7c6c7e4-9c9d-4d2b-95ab-5c299a959a3e.png)

Note the `Flags: 0x012 (SYN,ACK)`

We can add a filter for this flag like so `tcp.flags == 0x012` .

If we add this to our previous filter we will see all the  SYN,ACK responses from the Victims PC sent to Luciafer's PC/

`(ip.src == 192.168.100.103) && (ip.dst == 192.168.100.106) && (tcp.flags == 0x012)`

Then if we sort by the info column, we can scroll down and find all the open ports below 16384;

![image](https://user-images.githubusercontent.com/73170900/137886697-5eb97c4d-6630-4d45-b97f-5678f9574fbe.png)

These ports are `21, 135, 139, 445 and 3389`

## flag{21,135,139,445,3389}
