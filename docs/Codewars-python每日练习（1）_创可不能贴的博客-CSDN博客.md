<!--yml
category: codewars
date: 2022-08-13 11:47:16
-->

# Codewars-python每日练习（1）_创可不能贴的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_29060793/article/details/93161519?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-93161519.nonecase](https://blog.csdn.net/qq_29060793/article/details/93161519?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-93161519.nonecase)

# 1 Sum of the first nth term of Series

## Task:

Your task is to write a function which returns the sum of following series upto nth term(parameter).

> Series: 1 + 1/4 + 1/7 + 1/10 + 1/13 + 1/16 +…

## Rules:

You need to round the answer to 2 decimal places and return it as String.
If the given value is 0 then it should return 0.00
You will only be given Natural Numbers as arguments.

## Examples:

> SeriesSum(1) => 1 = “1.00”
> SeriesSum(2) => 1 + 1/4 = “1.25”
> SeriesSum(5) => 1 + 1/4 + 1/7 + 1/10 + 1/13 = “1.57”

* * *

## 我的解决方法：

```
def series_sum(n):
    if n == 0:
        return '%.2f' %n
    else:
        sum = 0
        for i in range(0, n):
            sum += 1/(1 + i*3)
        return '%.2f' %sum 
```

本题要注意限定浮点数的位数，返回值时应加上`'%.2f'`

* * *

## 其他优秀解决方法：

```
def series_sum(n):
    return '{:.2f}'.format(sum(1.0/(3 * i + 1) for i in range(n))) 
```

* * *

* * *

# 2 Printer Errors

## Task

In a factory a printer prints labels for boxes. For one kind of boxes the printer has to use colors which, for the sake of simplicity, are named with letters from a to m.

The colors used by the printer are recorded in a control string. For example a “good” control string would be aaabbbbhaijjjm meaning that the printer used three times color a, four times color b, one time color h then one time color a…

Sometimes there are problems: lack of colors, technical malfunction and a “bad” control string is produced e.g. aaaxbbbbyyhwawiwjjjwwm with letters not from a to m.

You have to write a function printer_error which given a string will output the error rate of the printer as a string representing a rational whose numerator is the number of errors and the denominator the length of the control string. Don’t reduce this fraction to a simpler expression.

The string has a length greater or equal to one and contains only letters from ato z.

* * *

## 我的解决方法:

```
def printer_error(s):
    count = 0
    for i in range(0, len(s)):
        if ord("m")< ord(s[i]) <= ord("z"):
            count += 1
    return str(count) + '/' + str(len(s)) 
```

将字符串转化为asc码使用`ord()`函数

* * *

## 其他优秀解决方法：

```
from re import sub
def printer_error(s):
    return "{}/{}".format(len(sub("[a-m]",'',s)),len(s)) 
```

re.sub()有替换功能

```
def printer_error(s):
    return "{}/{}".format(len([x for x in s if x not in "abcdefghijklm"]), len(s)) 
```

* * *

* * *