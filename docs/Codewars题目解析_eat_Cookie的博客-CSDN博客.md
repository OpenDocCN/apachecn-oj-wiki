<!--yml
category: codewars
date: 2022-08-13 11:26:25
-->

# Codewars题目解析_eat_Cookie的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_39088036/article/details/100095746?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-100095746.142^v40^control,185^v2^control](https://blog.csdn.net/qq_39088036/article/details/100095746?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-100095746.142^v40^control,185^v2^control)

最近刷了一些Codewars上的题目，整理如下，与大家分享一哈！

1.Roman Numerals Encoder

Create a function taking a positive integer as its parameter and returning a string containing the Roman Numeral representation of that integer.

Modern Roman numerals are written by expressing each digit separately starting with the left most digit and skipping any digit with a value of zero. In Roman numerals 1990 is rendered: 1000=M, 900=CM, 90=XC; resulting in MCMXC. 2008 is written as 2000=MM, 8=VIII; or MMVIII. 1666 uses each Roman symbol in descending order: MDCLXVI.

Example:

```
solution(1000) # should return 'M'
```

Help:

```
Symbol    Value
I          1
V          5
X          10
L          50
C          100
D          500
M          1,000
```

Remember that there can't be more than 3 identical symbols in a row.

题目大概意思说一下：给定一个正数n，把这个数用罗马数字表示出来。

思路分析：读完英文之后的你，一开始必定一头雾水。明白题目意思之后，首先的疑问是，这个转化规则怎么整呢？心里暗自问候一下出题者本人，然后继续陷入沉思...

为了弄明白这个规则，咱们看题，题目说罗马数字一列是不会有三个重复的数字的，开始举例。

1-I

2-II

3-III

4-IV

发现没有，还真的是这样，再继续举例

5-V

6-VI

7-VII

8-VIII

9-IX

哎？为什么这样表示呢？再看一下10-X，猜测这类数字应该是9=10-1，然后表示9的时候，把10和1倒过来表示。为了验证猜测，我们看900-CM，90-XC，猜想正确，表示规律的谜底已经被我们解开。

那么，如何用程序来进行这种转换呢？我们还是老思路，由特殊到一般：

比如说我们的数字是15，怎么才能把他转换到XV呢？15=10+5，由此我们想到可以用减去数字的方式获取15的数字组成。15-10=5，所以15代表的罗马数字一定有X，5-5=0，完结，所以15=XV。可以通过dictionary来设置数字和字符的对应关系。我们要注意一点，一定要从最大的数字开始减,比如15不能先15-5=10，那么前面开头的数字就是V，明显不对，因此我们要对dictionary中的值进行排序。我们用sorted函数进行排序。

```
def solution(n):
    # TODO convert int to roman string
    finalStr=""
    translationRule={1000:'M',900:'CM',500:'D',400:'CD',100:'C',90:'XC',50:'L',40:'XL',10:'X',9:'IX',5:'V',4:'IV',1:'I'}
    for x in sorted(translationRule.keys(),reverse=True):#reverse=true代表降序排列
        while n>=x:
            finalStr+=translationRule[x]
            n-=x
    return finalStr
```

代码比较简单，就不在详细说明了。

2.Sum of Digits / Digital Root

In this kata, you must create a `digital root` function.

A digital root is the *recursive sum of all the digits in a number.* Given *n*, take the sum of the digits of *n*. If that value has more than one digit, continue reducing in this way until a single-digit number is produced. This is only applicable to the natural numbers.

Here's how it works:

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

其实题意很明显了，例子已经告诉我们函数的功能是什么

思路：把给定整数的每一个位数单独拆分出来进行累加，然后判断一下是否已经为个位数。思路很简单，但是如果对python语法不熟悉的话，也会被绕进去。

注意：

6/10=0.6

6//10=0

在python中就是有这样的语法规则，第一种思路代码如下：

```
def digital_root(n):
    while n//10!=0 :
        temp=n;
        n=0;
        while temp!=0 :
          n=n+temp%10
          temp=temp//10
    return n
```

第二种思路：

运用python内置函数sum和map，代码如下：

```
def digital_root(n):
    # ...
    while n>9:
        n=sum(map(int,str(n)))#sum会对其中的可迭代对象，如：列表、元组、集合进行求和.
    return n
#map函数把大于9的整数全部变成单个整数，并用迭代器的形式进行存储
```