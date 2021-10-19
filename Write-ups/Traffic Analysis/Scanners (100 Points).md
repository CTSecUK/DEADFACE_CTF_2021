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

From our previous examinations of the PCAP file we know that the Victim's PC is using the IP address `192.168.100.103`

And that Luciafer's PC is using the IP Address `192.168.100.106`.
We can use the following filter to find traffic  between thos IP addresses
`((ip.src == 192.168.100.103) || (ip.dst == 192.168.100.106)) && ((ip.dst == 192.168.100.103) || (ip.dst == 192.168.100.106))`

![image](https://user-images.githubusercontent.com/73170900/137887708-d4de1951-feaf-421f-a691-d63df9cc84da.png)

Scrolling through the data we see traffic on many different ports.

![image](https://user-images.githubusercontent.com/73170900/137885534-8ddd29f2-3350-4bdb-9ff0-a0e1b3dee0e0.png)

In this screenshot, the red packets are ones where the port is closed, the grey packets we can see show the victims PC responding to the port scan to say that the port is open!

Taking a closer look at one of open port responses we can see;

![image](https://user-images.githubusercontent.com/73170900/137886001-a7c6c7e4-9c9d-4d2b-95ab-5c299a959a3e.png)

Note the `Flags: 0x012 (SYN,ACK)`

We can add a filter for this flag like so `tcp.flags == 0x012` .

We change our previous filter to olny show the SYN,ACK responses from the Victims PC sent to Luciafer's PC/

`(ip.src == 192.168.100.103) && (ip.dst == 192.168.100.106) && (tcp.flags == 0x012)`

Then if we sort by the info column, we can scroll down and find all the open ports below 16384;

![image](https://user-images.githubusercontent.com/73170900/137886697-5eb97c4d-6630-4d45-b97f-5678f9574fbe.png)

These ports are `21, 135, 139, 445 and 3389`

## flag{21,135,139,445,3389}
