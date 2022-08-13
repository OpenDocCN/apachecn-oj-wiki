<!--yml
category: codewars
date: 2022-08-13 11:43:44
-->

# codewars Kata——Take a Ten Minute Walk问题_Pray�的博客-CSDN博客

> 来源：[https://blog.csdn.net/Pray_21/article/details/109893816?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-109893816.nonecase](https://blog.csdn.net/Pray_21/article/details/109893816?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-109893816.nonecase)

# 大致思路

如果walk列表长度不为10，那么这个散步方案肯定是不能使我刚好准时回到原地的，那么就return False。如果walk长度为10，则设置初始坐标x=0，y=0，根据’n’ ‘s’ ‘e’ 'w’让y、x分别+1、-1，经过10次计算后，如果x和y同时为0，则回到原点，return True。否则return False。

# 代码

```
 """
codewars Kata: Take a Ten Minute Walk

Created on Sat Nov 21 11:25:14 2020

@author: Pray
"""

def is_valid_walk(walk):

    x=0
    y=0

    if(len(walk) != 10):
        return False
    else:
        for i in walk:
            if(i == 'n'):
                y = y + 1
            elif(i == 's'):
                y = y - 1
            elif(i == 'e'):
                x = x + 1
            elif(i == 'w'):
                x = x - 1
            else:
                pass
        if(x != 0 or y != 0):
            return False
        else:
            return True
    pass

walk = ['n','n','n','s','n','s','n','s','n','s']
print(is_valid_walk(walk)) 
```

# 更好的解决方案

在codewars上我看到了一个非常好的代码，只用了短短两行就实现了该功能，其主要思路是：要回到原点，就必须有’n’的个数='s’的个数，且’e’的个数='w’的个数。

代码如下：

```
def isValidWalk(walk):
    return len(walk) == 10 and walk.count('n') == walk.count('s') and walk.count('e') == walk.count('w') 
```