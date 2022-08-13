<!--yml
category: codewars
date: 2022-08-13 11:41:31
-->

# codewars Kata—— Primes in numbers问题_Pray�的博客-CSDN博客

> 来源：[https://blog.csdn.net/Pray_21/article/details/112132871?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-15-112132871-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/Pray_21/article/details/112132871?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-15-112132871-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 大致思路

首先定义一个函数用于判断某数是否为质数，判断思路是从2开始，到该数的平方根为止，遍历判断该数是否能被这些数整除，若能则不为质数，若都不能则为质数。

```
import math
def isPrime(n):
    sqr = int(math.sqrt(n))                                 
    if(n==1):return False                                   
    for i in range(2,sqr + 1):
        if(n % i ==0):return False                          
    return True 
```

然后利用递归调用的方法找出该数所有的质因数，代码如下：

```
def findPrimeFactors(n,dict_PrimeFactors):                  
    sqr = int(math.sqrt(n))
    if (isPrime(n)):                                        
        if str(n) in dict_PrimeFactors.keys():
            dict_PrimeFactors[str(n)] += 1
        else:
            dict_PrimeFactors[str(n)] = 1
    else:                                                   
        for i in range(1,sqr + 1):
            if(isPrime(i)):
                if(n%i == 0):
                    if str(i) in dict_PrimeFactors.keys():
                        dict_PrimeFactors[str(i)] += 1
                    else:
                        dict_PrimeFactors[str(i)] = 1
                    new_n = int(n/i)
                    findPrimeFactors(new_n,dict_PrimeFactors)
                    return dict_PrimeFactors

def prime_factors(n):                                       
    d_PrimeFactors = {}
    findPrimeFactors(n,d_PrimeFactors)
    prime_factors_str = ''
    for i in d_PrimeFactors.keys():
        if(d_PrimeFactors[i] > 1):
            temp_str = '(' + i + '**' + str(d_PrimeFactors[i]) + ')'
            prime_factors_str += temp_str
        else:
            prime_factors_str += '(' + i + ')'
    print(prime_factors_str) 
```

**以下是整体代码**

```
 """
codewars Kata: Primes in numbers

Created on Sun Jan  3 10:43:28 2021

@author: Pray
"""

import math
def isPrime(n):
    sqr = int(math.sqrt(n))                                 
    if(n==1):return False                                   
    for i in range(2,sqr + 1):
        if(n % i ==0):return False                          
    return True                                             

def findPrimeFactors(n,dict_PrimeFactors):                  
    sqr = int(math.sqrt(n))
    if (isPrime(n)):                                        
        if str(n) in dict_PrimeFactors.keys():
            dict_PrimeFactors[str(n)] += 1
        else:
            dict_PrimeFactors[str(n)] = 1
    else:                                                   
        for i in range(1,sqr + 1):
            if(isPrime(i)):
                if(n%i == 0):
                    if str(i) in dict_PrimeFactors.keys():
                        dict_PrimeFactors[str(i)] += 1
                    else:
                        dict_PrimeFactors[str(i)] = 1
                    new_n = int(n/i)
                    findPrimeFactors(new_n,dict_PrimeFactors)
                    return dict_PrimeFactors

def prime_factors(n):                                       
    d_PrimeFactors = {}
    findPrimeFactors(n,d_PrimeFactors)
    prime_factors_str = ''
    for i in d_PrimeFactors.keys():
        if(d_PrimeFactors[i] > 1):
            temp_str = '(' + i + '**' + str(d_PrimeFactors[i]) + ')'
            prime_factors_str += temp_str
        else:
            prime_factors_str += '(' + i + ')'
    return prime_factors_str 
```

# 网上大神的代码

看完大神的代码，又一次深感我在CSDN凑数的日子……

```
def primeFactors(n):
    ret = ''
    for i in range(2, n + 1):
        num = 0
        while(n % i == 0):
            num += 1
            n /= i
        if num > 0:
            ret += '({}{})'.format(i, '**%d' % num if num > 1 else '')
        if n == 1:
            return ret 
```