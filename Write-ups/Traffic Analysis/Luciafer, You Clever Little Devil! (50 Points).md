# Luciafer, You Clever Little Devil!
![Category](http://img.shields.io/badge/Category-Traffic_Analysis-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-50-brightgreen?style=for-the-badge)

## Details
>Luciafer gains access to the victim's computer by using the cracked password. What is the packet number of the response by the victim's system, saying that access is granted? Submit the flag as: `flag{#}`.
>
> NOTE: Use the packet response from her login, not from the password cracker.
>
> Use the PCAP from Monstrum ex Machina
---
Following on from the previous challenge (which can be founde [here](https://github.com/CTSecUK/DEADFACE_CTF_2021/blob/main/Write-ups/Traffic%20Analysis/Release%20the%20Crackin'!%20(50%20Points).md)

We can see the packet with the `Response: 230 user Logged in.` - packet number `159765`

![image](https://user-images.githubusercontent.com/73170900/137879438-f6f70dd4-4ee5-4790-af13-58a0541ec680.png)

## flag{159765}
