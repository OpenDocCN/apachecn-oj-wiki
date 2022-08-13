<!--yml
category: codewars
date: 2022-08-13 11:41:33
-->

# Codewars-You‘re a square!(Python)_YING0x00的博客-CSDN博客

> 来源：[https://blog.csdn.net/m0_46387669/article/details/107916739?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-16-107916739-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/m0_46387669/article/details/107916739?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-16-107916739-null-null.142^v40^control,185^v2^control&utm_term=codewars)

> 解法一：

```
def is_square(n):    
    if n<0:
        return False
    elif n == 0:
        return True
    else:
        i = 1
        while i < n:
            m = i*i
            if m == n:
                return True
            elif m>n:
                return False
            else:
                i+=1 
```