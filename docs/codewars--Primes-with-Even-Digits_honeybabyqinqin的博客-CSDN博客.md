<!--yml
category: codewars
date: 2022-08-13 11:49:32
-->

# codewars--Primes with Even Digits_honeybabyqinqin的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41871914/article/details/86377895?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-86377895.nonecase](https://blog.csdn.net/weixin_41871914/article/details/86377895?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-86377895.nonecase)

# Codewars–Stay away for many days

# Problem Description:

[点击此处获取题目](https://www.codewars.com/kata/primes-with-even-digits/python)
Find the closest prime number under a certain integer n that has the maximum possible amount of even digits.

For n = 1000, the highest prime under 1000 is 887, having two even digits (8 twice)

Naming f(), the function that gives that prime, the above case and others will be like the following below.

f(1000) —> 887 (even digits: 8, 8)

f(1210) —> 1201 (even digits: 2, 0)

f(10000) —> 8887

f(500) —> 487

f(487) —> 467

Features of the random tests:

Number of tests = 28
1000 <= n <= 5000000
![在这里插入图片描述](img/c2e87786f26b71861b84c4ecb85bd491.png)

* * *

# Solutions:

### Method1(By Myself):

```
import math
def f(num):
    lists={}
    flag = [1]*(num+2)
    p=2
    while(p<=num):
        count=0
        for i in list(str(p)): 
            if not int(i)%2:
                count+=1
        lists[p]=count
        for i in range(2*p,num+1,p):
            flag[i] = 0
        while 1:
            p += 1
            if(flag[p]==1):
                break
    if num in lists.keys():
        del lists[num]
    max_num=max(lists.values())
    list1=sorted(lists.items(),key=lambda item:item[1])
    list1.reverse()
    #print(list1)
    for j in list1:
        if j[1]==max_num:
            return j[0] 
```

#### Explanation(Method1):

## Method2:

```
from bisect import bisect_left as bisect

n = 5000000
sieve, PED, PED_DATA = [0]*((n>>1)+1), [], []
for i in range(3, n+1, 2):
    if not sieve[i>>1]:
        for j in range(i**2>>1, (n+1)>>1, i): sieve[j] = 1
        s = str(i)
        nEveD = sum(s.count(d) for d in "02468")
        if nEveD:
            PED.append(i)
            PED_DATA.append( (nEveD,len(s)-1) )

def f(n):
    idx = bisect(PED, n)-1
    m, (nEveD, l) = PED[idx], PED_DATA[idx]

    for c in range(idx):
        mc, (nEveDc, lc) = PED[idx-c], PED_DATA[idx-c]
        if nEveDc > nEveD:
            m, nEveD = mc, nEveDc
        if lc < nEveD: break
    return m 
```

## Method3:

```
def is_prime(n):
    if n % 2 == 0: return False
    for x in xrange(3, int(n**0.5) + 1, 2):
        if n % x == 0: return False
    return True

def f(n):
    max_prime, max_even_cnt = 0, 0

    for x in range(n-1, 0, -1):
        if len(str(x)) <= max_even_cnt + 1:
            break

        if is_prime(x):
            even_cnt = sum(d in "02468" for d in str(x))
            if even_cnt > max_even_cnt:
                max_prime = x
                max_even_cnt = even_cnt

    return max_prime 
```

## Method4:

```
import random

def is_probably_prime(n):
    if n > 1:
        for time in xrange(3):
            random_n = random.randint(2, n) - 1
            if pow(random_n, n - 1, n) != 1:
                return False
        return True
    return False

def is_prime(n):
    if is_probably_prime(n):
        if n < 2:
            return False
        elif n == 2:
            return True
        elif n % 2 == 0:
            return False
        for i in xrange(3, int(n ** 0.5) + 1, 2):
            if n % i == 0:
                return False
        return True
    return False

def f(n):
    max_prime, max_evens = 0, 0
    for i in xrange(n - 1, 1, -1):
        if len(str(i)) - 1 <= max_evens:
            break

        num_evens = sum(j in '02468' for j in str(i))
        if num_evens > 1 and is_prime(i):
            if num_evens > max_evens:
                max_prime = i
                max_evens = num_evens
    return max_prime 
```

### Gook luck! A happy ending!