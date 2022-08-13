<!--yml
category: codewars
date: 2022-08-13 11:46:18
-->

# Codewars第四天--Sum of Digits / Digital Root_soufal的博客-CSDN博客

> 来源：[https://blog.csdn.net/u011562123/article/details/81174720?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-81174720.nonecase](https://blog.csdn.net/u011562123/article/details/81174720?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-81174720.nonecase)

## Codewars第四天–Sum of Digits / Digital Root

题目描述：
`In this kata, you must create a digital root function.
A digital root is the recursive sum of all the digits in a number. Given n, take the sum of the digits of n. If that value has two digits, continue reducing in this way until a single-digit number is produced. This is only applicable to the natural numbers.
Here's how it works (Ruby example given):`

```
digital_root(16)
=> 1 + 6
=> 7

digital_root(942)
=> 9 + 4 + 2
=> 15 ...
=> 1 + 5
=> 6

digital_root(132189)
=> 1 + 3 + 2 + 1 + 8 + 9
=> 24 ...
=> 2 + 4
=> 6

digital_root(493193)
=> 4 + 9 + 3 + 1 + 9 + 3
=> 29 ...
=> 2 + 9
=> 11 ...
=> 1 + 1
=> 2
```

答案为：

```
def digital_root(n):
    while n >= 10:
        n=sum(map(int,str(n)))
        digital_root(n)
    return n
```

使用`map()` 函数会根据提供的函数对指定序列做映射。第一个参数 function 以参数序列中的每一个元素调用 function 函数，返回包含每次 function 函数返回值的新列表。
在这里需要先将输入的`int` 转换为`str` ，然后直接使用`sum()` 对字符串求和。在这里使用一个递归，计算一个新的值会判断其是否是两位数。