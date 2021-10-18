# The Count

![Category](http://img.shields.io/badge/Category-Programming-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-275-brightgreen?style=for-the-badge)

## Details
> Apparently DEADFACE is recruiting programmers, but spookyboi is a little apprehensive about recruiting amateurs. He's placed a password hash in the form of a flag for those able to solve his challenge. Solve the challenge and submit the flag as flag{SHA256_hash}.
> 
> [Link to Thread](https://ghosttown.deadface.io/t/what-programming-needs-are-there/56/4)
> 
> code.deadface.io:50000
---

Following the forum thread we see;

![image](https://user-images.githubusercontent.com/73170900/137820563-237f6647-b386-40a1-a7e3-ddfc69137e04.png)

Connecting to the shell we see;

```
❯ nc code.deadface.io 50000
DEADFACE gatekeeper: Let us see how good your programming skills are.
If a = 0, b = 1, c = 2, etc.. Tell me what the sum of this word is:

 You have 5 seconds to give me an answer.

Your word is: recondite
Too slow!! Word has been reset!
```

We therefore need to write a script to connect to the shell, receive the message and extract the word from it, calculate it's value and send it back to the shell with 5 seconds!

The below code deoes edcatly that!

```python
import socket

def get_letter_value(letter):
    alphabet_values = {'A':0, 'a':0, 'B':1, 'b':1, 'C':2, 'c':2, 'D':3,
                    'd':3, 'E':4, 'e':4, 'F':5, 'f':5, 'G':6, 'g':6,
                    'H':7, 'h':7, 'I':8, 'i':8, 'J':9, 'j':9, 'K':10,
                    'k':10, 'L':11, 'l':11, 'M':12, 'm':12, 'N': 13,
                    'n':13, 'O':14, 'o':14, 'P':15, 'p':15, 'Q':16,
                    'q':16, 'R':17, 'r':17, 'S':18, 's':18, 'T':19,
                    't':19, 'U':20, 'u':20, 'V':21, 'v':21, 'W':22,
                    'w':22, 'X':23, 'x':23, 'Y':24, 'y':24, 'Z':25, 'z':25 }
    value = alphabet_values[letter]
    return value 
 

TCP_IP = 'code.deadface.io'
TCP_PORT = 50000
BUFFER_SIZE = 1024
#MESSAGE = "Hello, World!"
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((TCP_IP, TCP_PORT))
#s.send(MESSAGE)
data = s.recv(BUFFER_SIZE)

challenge = data.split()
my_word = challenge[-1].decode("utf-8")
print("my word is:", my_word)

word_value = 0

for c in my_word:
    word_value = word_value + get_letter_value(c)

print("Value of word ", my_word, " is: ", word_value)

answer= (str(word_value).encode())

s.send(answer)

reponse = s.recv(BUFFER_SIZE)
print(reponse)

s.close()%  
```

Running the completed script we get;

```
❯ python count.py
my word is: reflective
Value of word  reflective  is:  95
b'\nflag{d1c037808d23acd0dc0e3b897f344571ddce4b294e742b434888b3d9f69d9944}\n'
```

## flagflag{d1c037808d23acd0dc0e3b897f344571ddce4b294e742b434888b3d9f69d9944}
