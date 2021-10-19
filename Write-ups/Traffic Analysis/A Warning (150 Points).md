# A Warning
![Category](http://img.shields.io/badge/Category-Traffic_Analysis-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-150-brightgreen?style=for-the-badge)

## Details
>Luciafer is being watched! Someone on the inside of Lytton Labs can see what she is doing and is sending her a message.
>
>One of them says: "Stay away from Lytton Labs... you have been warned."
>
>To find the flag, find the message. You'll know it when you see it. Submit the flag as `flag{flag-goes-here}`.
>
>Use the PCAP from LYTTON LABS 01 - Monstrum ex Machina.
---

First we try a search for the string `warning`. The first result that comes up is this one;

![image](https://user-images.githubusercontent.com/73170900/137890897-29275efb-6734-44db-bbfc-64bfb414d9a7.png)

Following the TCP stream on that packets yeailds the following;

![image](https://user-images.githubusercontent.com/73170900/137890995-823148ad-e65c-43a9-a682-c74a529628c8.png)

Now that we know the name of the file we can try to export it by selecting `File > Export Objects > HTTP`

![image](https://user-images.githubusercontent.com/73170900/137891037-48afe2a6-ef20-47d9-b54c-c2bd78250e7e.png)

Then filter the object list by the string `warning`

![image](https://user-images.githubusercontent.com/73170900/137891080-ace53013-7455-4247-94bf-ba515e3e2b4b.png)

Save the file and open it in your favouriute iumage viewer to reveal;

![image](https://user-images.githubusercontent.com/73170900/137891773-03916bcf-17f4-4471-b7e4-20bcb681e416.png)

## flag{angels-fear-to-tread}
