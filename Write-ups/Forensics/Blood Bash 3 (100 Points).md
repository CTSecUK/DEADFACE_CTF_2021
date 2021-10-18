# Blood Bash 3
![Category](http://img.shields.io/badge/Category-Forensics-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-100-brightgreen?style=for-the-badge)

## Details

>There's a flag on this system that we're having difficulty with. Unlike the previous flags, we can't seem to find a file with this flag in it. Perhaps the flag isn't stored in a traditional file?
>
> Username: `bl0ody_mary`
> Password: `d34df4c3`
>
> `bloodbash.deadface.io:22`
---

Connect to shell...

Run: `netstat -alnp`

```
bl0ody_mary@16ef1481fce1:~$ netstat -alnp
(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
udp        0      0 127.0.0.1:43526         0.0.0.0:*                           -                   
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name     Path

```

here we can see there is an open port listening on local server port `43526`

Also note UDP as the protocol at the begining of the line!

We connect via netcat to that port like so.. `nc -u 127.0.0.1 43526`

Hit `Enter key` and we get;

```
bl0ody_mary@16ef1481fce1:~$ nc -u 127.0.0.1 43526
^[[A^[[B
flag{open_port(al)s}
```

## flag{flag{open_port(al)s}}


Another unintended way to find the flag was as folllows...

Run: `sudo -l"`

```
bl0ody_mary@16ef1481fce1:~$ sudo -l
Matching Defaults entries for bl0ody_mary on 16ef1481fce1:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User bl0ody_mary may run the following commands on 16ef1481fce1:
    (ALL) NOPASSWD: /opt/start.sh, /usr/sbin/srv
```

If we try to  `cat /usr/sbin/srv`

```
bl0ody_mary@16ef1481fce1:~$ cat /usr/sbin/srv
cat: /usr/sbin/srv: Permission denied

```

Instead if we `cat /opt/start.sh`

```
bl0ody_mary@16ef1481fce1:~$ cat /opt/start.sh
#!/bin/bash

sudo /usr/sbin/srv &
exec /bin/bash

```

Notice at the end of the script it executes `/bin/bash` - as root!

run `sudo /opt/start.sh` gives us a root shell

```
root@16ef1481fce1:/home/bl0ody_mary#
```

Then if we `cat /usr/sbin/srv` we see;

```
#!/usr/bin/env python3

import socket as s
from binascii import hexlify as h, unhexlify as u

host = "127.0.0.1"
port = 43526
buffer = 1024

msg = b"666c61677b6f70656e5f706f727428616c29737d"
bytes_to_send = u(msg)

udp_server_socket = s.socket(s.AF_INET, s.SOCK_DGRAM)
udp_server_socket.bind((host, port))

while True:
        bytes_address_pair = udp_server_socket.recvfrom(buffer)
        #message = bytes_address_pair[0]
        address = bytes_address_pair[1]

        udp_server_socket.sendto(bytes_to_send, address)
```
If we use Python to decode the msg bytes, Again we can see the flag here!;

```
❯ python
Python 3.9.7 (default, Aug 31 2021, 13:28:12) 
[GCC 11.1.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> bytes.fromhex('666c61677b6f70656e5f706f727428616c29737d').decode("ascii")
'flag{open_port(al)s}'
```
