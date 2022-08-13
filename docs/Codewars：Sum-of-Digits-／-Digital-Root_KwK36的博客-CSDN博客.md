<!--yml
category: codewars
date: 2022-08-13 11:50:40
-->

# Codewars：Sum of Digits / Digital Root_KwK36的博客-CSDN博客

> 来源：[https://blog.csdn.net/KwK36/article/details/121143055?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-121143055.nonecase](https://blog.csdn.net/KwK36/article/details/121143055?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-121143055.nonecase)

# Codewars从零开始的python刷题路

## Sum of Digits / Digital Root

### 题目描述：

Digital root is the recursive sum of all the digits in a number.

Given n, take the sum of the digits of n. If that value has more than one digit, continue reducing in this way until a single-digit number is produced. The input will be a non-negative integer.

### 翻译：

数字根是数字中所有数字的递归和

给定n，取n中每位数字的和，如果它的数字多于一个，重复执行命令直到和为单个数字。输入为非负数字

### 解题代码

```
def digital_root(n):

    lis = [int(i) for i in str(n)]
    n = sum(lis)
    if n < 10:
        return n
    else:
        return digital_root(n) 
```

第一眼看到这个题就感觉非常适合用递归来做，但是或许没有必要搞得这么复杂。

其他解法：

```
def digital_root(n):

    while n>9:
        n=sum(map(int,str(n)))
    return n 
```