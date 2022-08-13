<!--yml
category: codewars
date: 2022-08-13 11:40:21
-->

# 【Codewars python 3kyu】：Last digit of a huge number_小菜鸟快飞的博客-CSDN博客_hrrf算法

> 来源：[https://blog.csdn.net/qq_36362028/article/details/100566509?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-15-100566509-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_36362028/article/details/100566509?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-15-100566509-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 问题描述：

For a given list `[x1, x2, x3, ..., xn]` compute the last (decimal) digit of `x1 ^ (x2 ^ (x3 ^ (... ^ xn)))`.

E. g.,

```
last_digit([3, 4, 2]) == 1
```

because `3 ^ (4 ^ 2) = 3 ^ 16 = 43046721`.

*Beware:* powers grow incredibly fast. For example, `9 ^ (9 ^ 9)` has more than 369 millions of digits. `lastDigit` has to deal with such numbers efficiently.

*Corner cases:* we assume that `0 ^ 0 = 1` and that `lastDigit` of an empty list equals to 1.

This kata generalizes [Last digit of a large number](http://www.codewars.com/kata/last-digit-of-a-large-number/haskell); you may find useful to solve it beforehand.

# 代码实现：

```
#codewars第二十八题
def last_digit(lst):
    n = 1
    for x in reversed(lst):
        # 如果直接写x ** (n % 4 + 4) ,当 n < 4 时结果就会出错
        n = x ** (n if n < 4 else n % 4 + 4) 
    return n % 10

# 另解一
from functools import reduce

def last_digit(lst):
    return reduce(lambda p, n: 1 if p == 0 or n == 1 else n if p == 1 or n == 0 else pow(n, p, 40) + 40, lst[::-1], 1) % 10

# 另解二
def last_digit(lst):
    if not lst:
        return 1
    else:
        out = 1
        for n in lst[len(lst):0:-1]:
            out = n**out
            if out > 2:
                out -= 2
                out %= 4
                out += 2
    return lst[0]**out% 10

last_digit([937640, 767456, 981242])
```