<!--yml
category: codewars
date: 2022-08-13 11:45:29
-->

# codewars Kata——RGB To Hex Conversion问题_Pray�的博客-CSDN博客

> 来源：[https://blog.csdn.net/Pray_21/article/details/112135879?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-112135879.nonecase](https://blog.csdn.net/Pray_21/article/details/112135879?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-112135879.nonecase)

# 代码

```
 """
codewars Kata: RGB To Hex Conversion

Created on Sun Jan  3 15:42:25 2021

@author: Pray
"""
def toHex(n):
    if(n <= 0): return '00'
    elif(n >= 255): return 'FF'
    a = int(n / 16)
    b = n % 16
    if (a > 9): a = chr(a + 55) 
    if (b > 9): b = chr(b + 55) 
    return str(a) + str(b)

def rgb(r, g, b):
    return toHex(r) + toHex(g) + toHex(b) 
```

# 网上大神的代码

```
def rgb(r, g, b):
    round = lambda x: min(255, max(x, 0))
    return ("{:02X}" * 3).format(round(r), round(g), round(b)) 
```