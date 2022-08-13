<!--yml
category: codewars
date: 2022-08-13 11:44:16
-->

# codewars Kata——Highest Scoring Word问题_Pray�的博客-CSDN博客

> 来源：[https://blog.csdn.net/Pray_21/article/details/109923306?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-109923306.nonecase](https://blog.csdn.net/Pray_21/article/details/109923306?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-109923306.nonecase)

# 大致思路和代码

这个题的思路上没有啥大问题，主要想记录下为每个字母打分的方法，这里利用了ord()函数来实现这一功能，下面我先介绍一下ord()函数

## ord()函数介绍

```
Help on built-in function ord in module builtins:

ord(c, /)
	Return the Unicode code point for a one-character string. 
```

ord() 函数是 chr() 函数（对于8位的ASCII字符串）或 unichr() 函数（对于Unicode对象）的配对函数，它以一个字符（长度为1的字符串）作为参数，返回对应的 ASCII 数值，或者 Unicode 数值，如果所给的 Unicode 字符超出了你的 Python 定义范围，则会引发一个 TypeError 的异常。

返回值是对应的十进制整数。

比如：

```
In [1]:print(ord('a'))
97 
```

## 代码

```
 """
codewars Kata: Highest Scoring Word

Created on Sun Nov 22 10:51:53 2020

@author: Pray
"""

def high(x):
    words = x.split(' ')
    h_score = 0
    score_temp = 0
    for word in words:
        score_temp = 0
        for i in word:
            score_temp += ord(i) - 96
        if(score_temp > h_score):
            h_score = score_temp
            h_string = word
    return h_string 
```

# 最简洁的实现方式

代码如下：

```
def high(x):
    return max(x.split(), key=lambda k: sum(ord(c) - 96 for c in k)) 
```

这里巧妙利用了max()函数中的key参数，以及lambda函数。

## max()函数

max()函数的帮助文档如下：

> max(…)
> max(iterable, *[, default=obj, key=func]) -> value
> max(arg1, arg2, *args, *[, key=func]) -> value
> With a single iterable argument, return its biggest item. The
> default keyword-only argument specifies an object to return if
> the provided iterable is empty.
> With two or more arguments, return the largest argument.

key参数是一个函数，它返回一个可比较的值供max()函数用于比较。
而key参数的配置这里利用了python自带的lambda函数。

## lambda函数

示例：

```
p = lambda x,y:x+y
print(p(4,6)) 
```