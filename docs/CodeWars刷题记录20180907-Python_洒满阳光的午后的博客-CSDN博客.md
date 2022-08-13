<!--yml
category: codewars
date: 2022-08-13 11:41:21
-->

# CodeWars刷题记录20180907-Python_洒满阳光的午后的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_32582203/article/details/82495892?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-10-82495892-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/sinat_32582203/article/details/82495892?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-10-82495892-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## 1、判断一个整数是否为完全平方数

我的解答：

```
import math

def is_square(n): 
    if n < 0:
        return False
    else:
        a = int(math.sqrt(n))
        return a*a == n 
```

漂亮解答：

```
import math
def is_square(n):
    return n > -1 and math.sqrt(n) % 1 == 0;
```

## 2、Mumbling

**Examples:**

```
accum("abcd")    # "A-Bb-Ccc-Dddd"
accum("RqaEzty") # "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
accum("cwAt")    # "C-Ww-Aaa-Tttt" 
```

The parameter of accum is a string which includes only letters from `a..z` and `A..Z`.

我的解答：

```
def accum(s):   
    if len(s) == 1:
        return s.upper()
    lowerStr = s.lower()
    res = lowerStr[0]
    for i in xrange(1,len(s)):
        res += '-' + lowerStr[i]*(i+1)
    return res.title()
```

漂亮解答：

```
def accum(s):
    return '-'.join(c.upper() + c.lower() * i for i, c in enumerate(s))
```

## 3、Strip Comments删除注释

Complete the solution so that it strips all text that follows any of a set of comment markers passed in. Any whitespace at the end of the line should also be stripped out.

**Example:**

Given an input string of:

```
apples, pears # and bananas
grapes
bananas !apples 
```

The output expected would be:

```
apples, pears
grapes
bananas 
```

The code would be called like so:

```
result = solution("apples, pears # and bananas\ngrapes\nbananas !apples", ["#", "!"])
# result should == "apples, pears\ngrapes\nbananas"
```

我的解答：

```
def solution(string, markers):
    strList = string.split('\n')
    for s in markers:
        strList = [v.split(s)[0].rstrip() for v in strList]
    return '\n'.join(strList)
```

 一种正则表示解法：

```
from re import split, escape

def solution(string, markers):
    if markers:
        pattern = "[" + escape("".join(markers)) + "]"
    else:
        pattern = ''
    return '\n'.join(split(pattern, line)[0].rstrip() for line in string.splitlines())
```

备注：这题最需要关注的是注释中包含注释的情况，例如：

> "apples, pears # and # bananas\ngrapes\nbananas !apples"