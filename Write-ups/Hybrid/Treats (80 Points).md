Treats
![Category](http://img.shields.io/badge/Category-Hybrid-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-80-brightgreen?style=for-the-badge)

## Details

>There is another flag associated with the site found in Depths. 
>
>Find the flag and submit it as: flag{flag-goes-here}.
---

https://ghosttown.deadface.io/t/potential-buyer-in-the-works/82


![image](https://user-images.githubusercontent.com/73170900/137755260-63cf46a9-57bc-4295-877c-76ec11e84dda.png)

The string `fkdgcbd7ctdqde5dhysmdgefrjs6ip2zjgiycx5vsdvtpdspmkhi5hid` posted by d34th is tor address

If we add a `.onion` extention and for like so `http:\\fkdgcbd7ctdqde5dhysmdgefrjs6ip2zjgiycx5vsdvtpdspmkhi5hid.onion`, then access in Tor browser we see a website.

This site seems fairly innocuous and most of the links do not work, but looking at the page sorce we can see some linked javascript files.

![image](https://user-images.githubusercontent.com/73170900/137818556-007168f5-2439-423a-867a-51f8686a94cc.png)

Examining those javascript files we see that one contains the following...

```
document.cookie = "flag{N0m_nom_c0ok13S}";

```

So the flag is;

## flag{N0m_nom_c0ok13S}
