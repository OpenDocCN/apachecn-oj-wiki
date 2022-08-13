<!--yml
category: codewars
date: 2022-08-13 11:33:31
-->

# codewars部分习题python代码（一）（难度：6kyu-8kyu）_知雨、的博客-CSDN博客_codewars python

> 来源：[https://blog.csdn.net/qq_43067159/article/details/110392884?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-110392884.142^v40^control,185^v2^control](https://blog.csdn.net/qq_43067159/article/details/110392884?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-110392884.142^v40^control,185^v2^control)

最近在刷codewars的python习题，花了三天刷到五级后，后面的题就不太会做了…所以我接下来记录一些题目的做法，以做笔记整理。学习他人的代码也是增长经验的过程。
注：括号里面的kyu代表题目难度，其中8级最简单，1级最难。
题目1：Multiples of 3 or 5(6kyu)
[题目网址](https://www.codewars.com/kata/514b92a657cdc65150000006)

> If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9\. The sum of these multiples is 23.Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in.Note: If the number is a multiple of both 3 and 5, only count it once. Also, if a number is negative, return 0(for languages that do have them)
> 大致题义：如果我们列出所有小于10的自然数中，3或5的倍数，我们可以得到3 5 6 9。这几个数的和为23。给一个数，返回所有小于它的自然数，3和5的倍数之和。如果其中有负数，则返回0。

我的基本思路是先遍历所有小于3和5的数，依次判断是否符合3或5的倍数，计算和。
我的答案

```
def solution(number):
    ans=0
    if number<0:
        ans=-1
    else:
        for i in range(1,number):
            if i%3==0 or i%5==0:
                ans+=i
    return ans 
```

题目2：Find the odd int(6kyu)
[题目链接](https://www.codewars.com/kata/54da5a58ea159efa38000836)
题目描述

> Given an array of integers, find the one that appears an odd number of times.
> There will always be only one integer that appears an odd number of times.
> 大致题义：给一串数字，找到那个出现了奇数次的数字（只有一个数字会出现集数次）

```
def find_it(seq):
    ans=0
    h=list(set(seq))
    for i in h:
        if seq.count(i)%2==1:
            return i 
```

题目3：Vowel Count(7kyu)
[题目网址](https://www.codewars.com/kata/54ff3102c1bad923760001f3)

> Return the number (count) of vowels in the given string.We will consider a, e, i, o, u as vowels for this Kata (but not y).The input string will only consist of lower case letters and/or spaces.
> 大致题义：数字符串中出现a,e,i,o,u的次数

```
def get_count(input_str):
    num_vowels = 0
    h=['a','e','i','o','u']
    for i in h:
        num_vowels+=input_str.count(i)
    return num_vowels 
```

最高票代码：只用了两行

```
def getCount(inputStr):
    return sum(1 for let in inputStr if let in "aeiouAEIOU") 
```

题目4：Sum of Digits / Digital Root（6kyu）
[题目网址](https://www.codewars.com/kata/541c8630095125aba6000c00)

> Digital root is the recursive sum of all the digits in a number.
> Given n, take the sum of the digits of n. If that value has more than one digit, continue reducing in this way until a single-digit number is produced. The input will be a non-negative integer.
> Examples
> 16 --> 1 + 6 = 7
> 942 --> 9 + 4 + 2 = 15 --> 1 + 5 = 6
> 132189 --> 1 + 3 + 2 + 1 + 8 + 9 = 24 --> 2 + 4 = 6
> 493193 --> 4 + 9 + 3 + 1 + 9 + 3 = 29 --> 2 + 9 = 11 --> 1 + 1 = 2

我的思路，首先先写一个函数，能计算各位之和。然后再循环，到最终结果小于10为止。（略）
各位大佬的解答：

最最强的一个：

```
def digital_root(n):
    return n%9 or n and 9 
```

实话说我花了好几分钟才明白为啥这么写o(╥﹏╥)o

今天先更新到这儿。今天的题都比较简单。