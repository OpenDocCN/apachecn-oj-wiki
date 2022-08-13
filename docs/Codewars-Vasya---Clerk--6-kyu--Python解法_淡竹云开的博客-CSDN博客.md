<!--yml
category: codewars
date: 2022-08-13 11:41:10
-->

# Codewars Vasya - Clerk--6 kyu--Python解法_淡竹云开的博客-CSDN博客

> 来源：[https://blog.csdn.net/zhangpeterx/article/details/103095360?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-103095360.142^v40^control,185^v2^control](https://blog.csdn.net/zhangpeterx/article/details/103095360?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-103095360.142^v40^control,185^v2^control)

Codewars Vasya - Clerk–6 kyu–Python解法

* * *

Codewars 是一个跟LeetCode类似的结题网站。
Codewars题解专栏：[Codewars题解](https://zhang0peter.blog.csdn.net/category_9516538.html)

* * *

题目地址：[Train: Vasya - Clerk | Codewars](https://www.codewars.com/kata/vasya-clerk/train/python)

* * *

The new “Avengers” movie has just been released! There are a lot of people at the cinema box office standing in a huge line. Each of them has a single 100, 50 or 25 dollar bill. An “Avengers” ticket costs 25 dollars.

Vasya is currently working as a clerk. He wants to sell a ticket to every single person in this line.

Can Vasya sell a ticket to every person and give change if he initially has no money and sells the tickets strictly in the order people queue?

Return YES, if Vasya can sell a ticket to every person and give change with the bills he has at hand at that moment. Otherwise return NO.

Examples:

```
tickets([25, 25, 50]) # => YES 
tickets([25, 100]) # => NO. Vasya will not have enough money to give change to 100 dollars
tickets([25, 25, 50, 50, 100]) # => NO. Vasya will not have the right bills to give 75 dollars of change (you can't make two bills of 25 from one of 50) 
```

* * *

这道题目是`6kyu`难度的，比较简单。
Python解法如下：

```
def tickets(people):
    l=[0,0]
    for i in people:
        if i==25:
            l[0]+=1
        elif i==50:
            if l[0]==0:
                return "NO"
            else:
                l[0]-=1
                l[1]+=1
        else:
            if l[1]>=1:
                if l[0]==0:
                    return "NO"
                else:
                    l[0]-=1
                    l[1]-=1
            else:
                if l[0]<3:
                    return "NO"
                else:
                    l[0]-=3
    return "YES" 
```

上面的解法是比较啰嗦的，简化后别人的解法参考如下：

```
def tickets(a):
    n25 = n50 = n100 = 0
    for e in a:
        if   e==25            : n25+=1
        elif e==50            : n25-=1; n50+=1
        elif e==100 and n50>0 : n25-=1; n50-=1
        elif e==100 and n50==0: n25-=3
        if n25<0 or n50<0:
            return 'NO'
    return 'YES' 
```