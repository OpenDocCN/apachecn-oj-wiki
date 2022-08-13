<!--yml
category: codewars
date: 2022-08-13 11:38:50
-->

# codewars Kata——Moving Zeros To The End问题_Pray�的博客-CSDN博客

> 来源：[https://blog.csdn.net/Pray_21/article/details/110366754?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-8-110366754-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/Pray_21/article/details/110366754?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-8-110366754-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 大体思路和代码

刚开始读题的时候很快就有了思路：每一轮用list的index方法找到第一个为0的元素的索引，然后将该元素弹出(pop)，在将其添加(append)在列表末尾。于是我很快写出了代码并进行test，但是发现出现了2个结果报错。

我一看，嗷，原来是佐田……咳咳，原来是这两个test案例中提供的数组包含元素False，而False所属的bool数据类型实际上是int的一个子类(subclass)，所以代码在整理数组时会把False也搬运到末尾，但是根据该题目的要求，False不应该算作0。

于是，我的解决思路变为了：另外编写一个函数判断某一元素是否为0且不为False，该函数主要是利用type方法进行判断。然后在move_zeros函数里进行遍历，但是遍历顺序应为倒序（具体原因大家可以自己体会），然后将每次遇到的0元素弹出并加在列表末尾。

代码如下：

```
 """
codewars Kata: Moving Zeros To The End

Created on Mon Nov 30 08:11:46 2020

@author: Pray
"""

def is_zero(v):
    return type(v) in (int,float) and not v

def move_zeros(array):
    for i in reversed(range(len(array))):
        if(is_zero(array[i])):
            array.append(array.pop(i))
    return array 
```

# 大神的解决方案

接下来让我们鉴赏一下大神们的解决方案叭

## 大神方案一

```
def move_zeros(arr):
    l = [i for i in arr if isinstance(i, bool) or i!=0]
    return l+[0]*(len(arr)-len(l)) 
```

第一位大神利用了isinstance函数，先将列表中所有0元素剔除出去，然后在列表后面添加相应个数的0元素，代码非常的简洁易懂，非常的amazing啊。

## 大神方案二

```
def move_zeros(array):
    return sorted(array, key=lambda x: x==0 and type(x) is not bool) 
```

如果说第一位大神的代码更为简洁，那第二位大神的代码就更富于技巧性了。这位大神的lambda函数用得非常熟练。
lambda函数的用法不过多介绍啦，sorted函数的具体用法我确实是不太熟练，大家可以看看下面这个链接中的介绍，非常详细：
[Python sorted函数详解(高级篇)](https://www.cnblogs.com/shen-qiang/p/11801983.html)