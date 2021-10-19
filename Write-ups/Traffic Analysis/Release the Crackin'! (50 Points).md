# Release the Crackin'!
![Category](http://img.shields.io/badge/Category-Traffic_Analysis-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-50-brightgreen?style=for-the-badge)

## Details

>Luciafer cracked a password belonging to the victim. Submit the flag as: `flag{password}`.
>
> Use the PCAP from LYTTON LABS 01 - Monstrum ex Machina.
---

First we filter the packet list to show FTP related packets

![image](https://user-images.githubusercontent.com/73170900/137879522-9f15bf26-e252-4dc9-a47e-275631942413.png)


Scrolling through the packets we notice several login attempts agains a user `cgeschickter` with mulitple passwoprd attempts.


![image](https://user-images.githubusercontent.com/73170900/137879290-14c60792-37a0-4748-b9f5-a28ad83042da.png)

Further down the list, we can see that one is successful!

![image](https://user-images.githubusercontent.com/73170900/137879438-f6f70dd4-4ee5-4790-af13-58a0541ec680.png)

Therfore the flag is;

## flag{darkangel}

