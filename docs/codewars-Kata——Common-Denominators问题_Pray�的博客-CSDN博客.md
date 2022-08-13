<!--yml
category: codewars
date: 2022-08-13 11:41:00
-->

# codewars Kata——Common Denominators问题_Pray�的博客-CSDN博客

> 来源：[https://blog.csdn.net/Pray_21/article/details/112134827?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-3-112134827-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/Pray_21/article/details/112134827?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-3-112134827-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 问题描述

这道题通俗来讲就是要求你对一系列分数进行通分，而且通分后的分母应该是这些原分数分母的最小公倍数。所以此题的解题核心在于求取最小公倍数的算法。

# 思路与代码

我们采用曲线救国的方针，先求取分母们的最大公因数（Greatest Common Divisor, gcd），然后基于最大公倍数求取最小公倍数。这个思路也很好理解，假设存在两数 a a a和 b b b，二者的最大公因数为 g c d ( a , b ) gcd(a,b) gcd(a,b)，则 a a a和 b b b的最大公倍数即为
a ∗ b / g c d ( a , b ) a*b/gcd(a,b) a∗b/gcd(a,b)
对于多个数求最小公倍数，则可以先求前 2 2 2个数的最小公倍数，再用前 2 2 2个数的最小公倍数与第3个数用相同的算法求取最小公倍数，以此类推即可。
至于如何求取最大公倍数gcd，则可以采取辗转相除法，具体算法不过多介绍，大家可以参看以下链接，查看辗转相除法具体原理：
[欧几里得算法(辗转相除法)](https://baike.baidu.com/item/%E6%AC%A7%E5%87%A0%E9%87%8C%E5%BE%97%E7%AE%97%E6%B3%95/1647675?fromtitle=%E8%BE%97%E8%BD%AC%E7%9B%B8%E9%99%A4%E6%B3%95&fromid=4625352&fr=aladdin)

**代码如下**

```
 """
codewars Kata: Common Denominators

Created on Sun Jan  3 14:07:42 2021

@author: Pray
"""

a = [[1, 2], [1, 3], [1, 4]]

def find_gcd(a,b):
    if (a<b):a,b=b,a
    while(b!=0):
        c=a
        a=b
        b=c%b
    gcd=a
    return gcd

def convertFracts(lst):
    if(len(lst)>=2):
        D = lst[0][1] * lst[1][1] / find_gcd(lst[0][1],lst[1][1])
        for i in range(2,len(lst)):
            D = D * lst[i][1] / find_gcd(D,lst[i][1])
        D=int(D)
        new_lst=[]
        for i in range(len(lst)):
            temp_lst = [lst[i][0] * int(D / lst[i][1]),D]
            new_lst.append(temp_lst)
        return new_lst
    else:
        return lst

print(convertFracts(a)) 
```

# 网上大神的代码

提交了这个Kata之后，我才发现，原来python的math库中是有计算最大公因数的这个函数的……是我愚鲁了
**代码如下**

```
import math
import functools

def convertFracts(lst):
    lcm = lambda a, b : abs(a*b) // math.gcd(a, b)
    tmp_list = list(map(lambda x : x[1] ,list(lst)))
    lcm_num = functools.reduce(lcm,tmp_list)
    return list(map(lambda x : [x[0] * lcm_num // x[1], lcm_num] , list(lst))) 
```