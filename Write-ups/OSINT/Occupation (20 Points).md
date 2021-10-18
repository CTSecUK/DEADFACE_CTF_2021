# Occupation 
![Category](http://img.shields.io/badge/Category-OSINT-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-20-brightgreen?style=for-the-badge)

## Details

> Which employee at De Monne Financial was the target of DEADFACE that resulted in a data leak? Submit the employee's job title as the flag: `flag{Job Title}`
---

I we look at the gostTown forum we find the folwoijg thread - [https://ghosttown.deadface.io/t/they-got-the-wrong-guy/75](https://ghosttown.deadface.io/t/they-got-the-wrong-guy/75)

Ths thread links to an external news article - [https://www.worldgreynews.com/details/168914/de-monne-senior-organizer-on-administrative-leave-pending-data-leak-investigation](https://www.worldgreynews.com/details/168914/de-monne-senior-organizer-on-administrative-leave-pending-data-leak-investigation)

The title of this article is;

> "De Monne **Senior Organizer** On Administrative Leave Pending Data Leak Investigation" 

## flag{Senior Organizer}``python
#!/usr/bin/env python3
from binascii import unhexlify as u

def get_flag():
    flag = '666c61677b30682d6c6f6f6b2d612d466c61477d'
    return u(flag).decode('utf-8')


print(f'The flag is: ')
```

At the moment this code never calls the **get_flag()** funtion. it just defines it.

If we change the bottom line of code to `print(get_flag())`

Then run the script we get....

## flagflag{0h-look-a-FlaG}
