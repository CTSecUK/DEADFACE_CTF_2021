# Luciafer's Fatal Error
![Category](http://img.shields.io/badge/Category-Traffic_Analysis-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-50-brightgreen?style=for-the-badge)

## Details

```python
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
