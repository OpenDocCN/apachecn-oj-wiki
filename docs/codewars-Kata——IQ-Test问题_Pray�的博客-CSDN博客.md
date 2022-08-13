<!--yml
category: codewars
date: 2022-08-13 11:41:49
-->

# codewars Kata——IQ Test问题_Pray�的博客-CSDN博客

> 来源：[https://blog.csdn.net/Pray_21/article/details/109921134?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-24-109921134-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/Pray_21/article/details/109921134?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-24-109921134-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 实现思路和代码

由于输入给定是一个字符串，每个数字之间用空格间隔开，所以先对字符串进行分割和转int的操作，然后遍历数组，查看每个数的奇偶性，统计奇数和偶数的个数，同时分别将第一次出现的奇偶数的索引进行记录。最后判断奇偶数的数量，给出目标的索引。

代码如下：

```
 """
codewars Kata: IQ Test

Created on Sun Nov 22 09:24:31 2020

@author: Pray
"""

def iq_test(numbers):
    n_odd = 0
    n_even = 0
    d = dict()
    number_list = numbers.split(' ')
    for i in range(len(number_list)):
        num = int(number_list[i])
        if(num%2 == 0):
            n_even = n_even + 1
            if 'even' not in d.keys():
                d['even'] = i + 1
        else:
            n_odd = n_odd + 1
            if 'odd' not in d.keys():
                d['odd'] = i + 1
    if(n_even > n_odd):
        return d['odd']
    else:
        return d['even']

numbers = "1 2 1 1"
print(iq_test(numbers)) 
```

# 其他的实现方式

网上的思路大同小异。这里主要放一些更加简洁有效的实现方式。
下面要介绍的一个解决方案可以很简洁地实现这一功能。其思路是根据数组中每一个数是否偶数建立一个同样大小的由bool变量组成的列表，通过对这个bool列表中的True和False进行计数（list.count）来找到目标对应的索引。这里主要是要掌握一些列表的方法，他们可以作为编程技巧大大提高我们的编程效率。

代码如下：

```
def iq_test(numbers):
    e = [int(i) % 2 == 0 for i in numbers.split()]

    return e.index(True) + 1 if e.count(True) == 1 else e.index(False) + 1 
```