<!--yml
category: codewars
date: 2022-08-13 11:42:41
-->

# codewars Kata——Product of consecutive Fib numbers问题_Pray�的博客-CSDN博客

> 来源：[https://blog.csdn.net/Pray_21/article/details/110087194?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-21-110087194-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/Pray_21/article/details/110087194?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-21-110087194-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 思路与代码

思路其实很简单，我们已知斐波那契数列是给定两个边界条件（初始值），然后按照F(n+1)=F(n)+F(n-1)的方式递推得到，那么我可以从先给定0，1的初始条件，然后开始逐轮试探，每一轮我们先判断F(n)*F(n+1)<prod是否成立，只要成立，就更新当前的F(n)和F(n+1)，并继续下一轮，这样的逐轮尝试进行到F(n)*F(n+1)≥prod为止，然后返回此时的F(n)、F(n+1)以及F(n)*F(n+1)==prod的bool值。

代码如下：

```
 """
codewars Kata: Product of consecutive Fib numbers

Created on Tue Nov 24 16:53:05 2020

@author: Pray
"""

def productFib(prod):
    a = 0
    b = 1
    while (a*b < prod):
        c = a
        a = b
        b = c + b
    return [a, b, prod == a*b] 
```

提交代码后我看到了网上其他大神的解决方法，我发现代码可以进一步优化变得更为简洁，主要是可以在F(n)和F(n+1)更新那一步简化代码写法，改写为：

```
[a, b]=[b, a + b] 
```

这样改写代码效果是一样的，但是整体代码书写会更为简洁