<!--yml
category: codewars
date: 2022-08-13 11:42:52
-->

# codewars Kata——Ones and Zeros问题_Pray�的博客-CSDN博客

> 来源：[https://blog.csdn.net/Pray_21/article/details/109894320?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-27-109894320-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/Pray_21/article/details/109894320?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-27-109894320-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 我的实现方法

我的实现方法很简单，直接上代码：

```
 """
codewars Kata: Ones and Zeros

Created on Sat Nov 21 12:02:19 2020

@author: Pray
"""

def binary_array_to_number(arr):
    sum = 0
    for i in range(len(arr)):
        sum = sum + arr[i] * 2**(len(arr)-i-1)
    return sum 
```

# 更为高明的实现

在Kata的solutions中我看到了跟我给高明的实现方法，利用了int函数。具体用法参考如下文档：

```
class int(object)
 |  int([x]) -> integer
 |  int(x, base=10) -> integer
 |  
 |  Convert a number or string to an integer, or return 0 if no arguments
 |  are given.  If x is a number, return x.__int__().  For floating point
 |  numbers, this truncates towards zero.
 |  
 |  If x is not a number or if base is given, then x must be a string,
 |  bytes, or bytearray instance representing an integer literal in the
 |  given base.  The literal can be preceded by '+' or '-' and be surrounded
 |  by whitespace.  The base defaults to 10\.  Valid bases are 0 and 2-36.
 |  Base 0 means to interpret the base from the string as an integer literal.
 |  >>> int('0b100', base=0)
 |  4 
```

那么应用到该题，解决方案如下：

```
def binary_array_to_number(arr):
    return int(''.join(str(a) for a in arr), 2) 
```