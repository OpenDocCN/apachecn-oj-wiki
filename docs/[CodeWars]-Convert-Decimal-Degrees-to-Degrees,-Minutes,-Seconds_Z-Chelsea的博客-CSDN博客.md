<!--yml
category: codewars
date: 2022-08-13 11:37:56
-->

# [CodeWars] Convert Decimal Degrees to Degrees, Minutes, Seconds_Z Chelsea的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_51047199/article/details/120382371?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-11-120382371-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_51047199/article/details/120382371?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-11-120382371-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# CodeWars 里的7kyu题目 Convert Decimal Degrees, Minutes, Seconds

## 题目说明：

Description:
Convert Decimal Degrees to Degrees, Minutes, Seconds.

Remember: 1 degree = 60 minutes; 1 minute = 60 seconds.

Input: Positive number.

Output: Array [degrees, minutes, seconds]. E.g [30, 25, 25]

Trailing zeroes should be omitted in the output. E.g

convert (50)
//correct output -> [50]
//wrong output -> [50, 0, 0]

convert(80.5)
//correct output -> [ 80, 30 ]
//wrong output -> [80, 30, 0]

convert(0.0001388888888888889)
//correct output -> [ 0, 0, 1 ]
//wrong output -> [1]
Round the seconds to the nearest integer.

## python解决方法：

代码：

```
def convert(degrees):
    l = []
    h = int(degrees // 1)
    degrees = (degrees % 1) * 60
    m = int(degrees // 1)
    degrees = (degrees - m) * 60
    s = int(degrees // 1)
    if degrees % 1 > 0.5:
        s = s + 1
    if s == 60:
        m = m + 1
        s = 0
    if m == 60:
        h = h + 1
        m = 0
    if s == 0:
        if m == 0:
            l.append(h)
        else:
            l = [h, m]
    else:
        l = [h, m, s]
    return l 
```