<!--yml
category: codewars
date: 2022-08-13 11:43:31
-->

# 入坑codewars第11天-Clock in Mirror_渣渣琪的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_37341950/article/details/84937329?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-84937329.nonecase](https://blog.csdn.net/sinat_37341950/article/details/84937329?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-84937329.nonecase)

题目一：

Peter can see a clock in the mirror from the place he sits in the office. When he saw the clock shows 12:22

He knows that the time is 11:38

in the same manner:

05:25 --> 06:35

01:50 --> 10:10

11:58 --> 12:02

12:01 --> 11:59

Please complete the function `WhatIsTheTime(timeInMirror)`, where `timeInMirror` is the mirrored time (what Peter sees) as string.

Return the *real* time as a string.

Consider hours to be between 1 <= hour < 13.

So there is no 00:20, instead it is 12:20.

There is no 13:20, instead it is 01:20.

题意：

```
题目意思是：
已知在镜子里看到的时间，求真实的时间。
```

解题思路：

```
我的思路是：
因为我们知道镜子里的时针、分针是关于y轴对称；
因此设x是镜子里的时钟数，y是分针数
则：实际时钟数a=11-(x%12),b=60-y
但是有几种特殊情况：比如12:00和08:00这样的情况要特殊处理，具体看代码： 
```

代码如下：

```
import re
def what_is_the_time(time_in_mirror):
    y=re.findall(r":(.+)",time_in_mirror)
    x=re.findall(r"(.+?):",time_in_mirror)
    a=11-(int(x[0])%12)
    b=60-int(y[0])
    hour=str(a)
    minute=str(b)
    if a==0:hour='12' #处理小时为12但是计算结果计算出是0
    if a<10 and a!=0: #处理<10的情况，要前面加0
        hour='0'+str(a)
    if b==60: #处理计算结果分钟是60的情况，要考虑12:00的特殊情况
        minute='00'
        a=a+1
        hour=str(a)
        if a<10:
            hour='0'+str(a)

    if b<10 and b!=0: #同理处理分针小于10的情况
        minute='0'+str(b)
    c=hour+':'+minute
    return c
```

看看大神的精简代码：

```
def what_is_the_time(time_in_mirror):
    h, m = map(int, time_in_mirror.split(':'))
    return '{:02}:{:02}'.format(-(h + (m != 0)) % 12 or 12, -m % 60)
```

（1）大神代码运用map()函数：

map函数怎么用？

```
>>>def square(x) :            # 计算平方数
...     return x ** 2
... 
>>> map(square, [1,2,3,4,5])   # 计算列表各个元素的平方
[1, 4, 9, 16, 25]
>>> map(lambda x: x ** 2, [1, 2, 3, 4, 5])  # 使用 lambda 匿名函数
[1, 4, 9, 16, 25]

# 提供了两个列表，对相同位置的列表数据进行相加
>>> map(lambda x, y: x + y, [1, 3, 5, 7, 9], [2, 4, 6, 8, 10])
[3, 7, 11, 15, 19]
```

（2）还用到了python中取余的特殊性

```
以-3 % 4为例：

q = ⌊-3/4⌋ = ⌊-0.75⌋ = -1

因此，余数r = a - nq = -3 - (-1 * 4) = 1

此实现有如下特点：

1\. 余数的符号与除数相同

2\. 这种实现在某些地方被称之为求余
```

（3）还用到了or的特性：

如果前面为真则不执行or后的，如果前面为假才执行or后面的，真的巧妙!!!