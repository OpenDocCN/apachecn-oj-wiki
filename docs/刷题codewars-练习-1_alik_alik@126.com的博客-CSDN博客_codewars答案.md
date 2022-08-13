<!--yml
category: codewars
date: 2022-08-13 11:47:56
-->

# 刷题codewars 练习-1_alik_alik@126.com的博客-CSDN博客_codewars答案

> 来源：[https://blog.csdn.net/m0_55276534/article/details/114799884?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-114799884.nonecase](https://blog.csdn.net/m0_55276534/article/details/114799884?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-114799884.nonecase)

## 刷题codewars 练习-1

## Count characters in your string：计算字符串中单字（6kyu）

## 介绍：

主要思想是计算字符串中所有出现的字符。如果您有类似的字符串aba，
则结果应为{‘a’: 2, ‘b’: 1}。

如果字符串为空怎么办？然后，结果应为空对象文字{}。

## 自己练习：

```
 def count(string):
    result={}
    for i in string:
        result[i]=string.count(i)
    return out 
```

## 参考答案-1

```
 def count(string):

    return {i: string.count(i) for i in string} 
```

## 参考答案-2

```
from collections import Counter as count 
```

[www.codewars转载地址](https://www.codewars.com/kata/52efefcbcdf57161d4000091/train/python)