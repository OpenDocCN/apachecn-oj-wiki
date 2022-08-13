<!--yml
category: codewars
date: 2022-08-13 11:45:27
-->

# codewars Kata——Persistent Bugger问题_Pray�的博客-CSDN博客

> 来源：[https://blog.csdn.net/Pray_21/article/details/109922003?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-109922003.nonecase](https://blog.csdn.net/Pray_21/article/details/109922003?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-109922003.nonecase)

# 大致思路和代码

本人解决这一问题的关键思想是函数的递归调用，递归思想及如何实现大家可以自行百度，大致思路就是从上到小不断逐级调用自身，最终调用到底层，即n为一位数时，然后再逐级向上返回值，逐级加一，最后就可以得到persistentence的值了。

话不多说，放代码：

```
 """
codewars Kata: Persistent Bugger

Created on Sun Nov 22 09:58:35 2020

@author: Pray
"""

def persistence(n):
    if(len(str(n)) == 1):
        return 0
    else:
        new_n = 1
        for i in range(len(str(n))):
            new_n = new_n * int(str(n)[i])
        return persistence(new_n) + 1 
```

# 其他解决方案

上面我是用了递归的方法实现了计数的累加，但其实python中的ruduce函数可以使代码变得更加简洁。

## reduce函数介绍

### 描述

reduce() 函数会对参数序列中元素进行累积。

函数将一个数据集合（链表，元组等）中的所有数据进行下列操作：用传给 reduce 中的函数 function（有两个参数）先对集合中的第 1、2 个元素进行操作，得到的结果再与第三个数据用 function 函数运算，最后得到一个结果。

### 语法

```
reduce(function, iterable[, initializer]) 
```

### 参数

```
function -- 函数，有两个参数
iterable -- 可迭代对象
initializer -- 可选，初始参数 
```

### 返回值

返回函数计算结果。

### 示例

```
>>>def add(x, y) :            
...     return x + y
... 
>>> reduce(add, [1,2,3,4,5])   
15
>>> reduce(lambda x, y: x+y, [1,2,3,4,5])  
15 
```

## 利用ruduce函数解决该问题

直接上代码：

```
import operator
from functools import reduce
def persistence(n):
    i = 0
    while n>=10:
        n=reduce(operator.mul,[int(x) for x in str(n)],1)
        i+=1
    return i 
```

注意这里有个问题，在python3版本中，直接使用reduce()的话，系统会报错，提示不存在reduce()函数。

这是因为在Python 3里，reduce() 函数已经被从全局名字空间里移除了，它现在被放置在fucntools 模块里。使用前需要先import，即：

```
from functools import reduce 
```