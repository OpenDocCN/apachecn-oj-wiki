<!--yml
category: codewars
date: 2022-08-13 11:45:00
-->

# 入坑codewars第18天-Alphabet wars - nuclear strike_渣渣琪的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_37341950/article/details/85125182?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-85125182.nonecase](https://blog.csdn.net/sinat_37341950/article/details/85125182?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-85125182.nonecase)

题目：Alphabet wars - nuclear strike

# Introduction

There is a war and nobody knows - the alphabet war!
The letters hide in their nuclear shelters. The nuclear strikes hit the battlefield and killed a lot of them.

# Task

Write a function that accepts `battlefield` string and returns letters that survived the nuclear strike.

*   The `battlefield` string consists of only small letters, `#`,`[` and `]`.
*   The nuclear shelter is represented by square brackets `[]`. The letters inside the square brackets represent letters inside the shelter.
*   The `#` means a place where nuclear strike hit the battlefield. If there is at least one `#` on the battlefield, all letters outside of shelter die. When there is no any `#` on the battlefield, all letters survive (but do not expect such scenario too often ;-P ).
*   The shelters have some durability. When 2 or more `#` hit close to the shelter, the shelter is destroyed and all letters inside evaporate. The 'close to the shelter' means on the ground between the shelter and the next shelter (or beginning/end of battlefield). The below samples make it clear for you.

# Example

```
abde[fgh]ijk     => "abdefghijk"  (all letters survive because there is no # )
ab#de[fgh]ijk    => "fgh" (all letters outside die because there is a # )
ab#de[fgh]ij#k   => ""  (all letters dies, there are 2 # close to the shellter )
##abde[fgh]ijk   => ""  (all letters dies, there are 2 # close to the shellter )
##abde[fgh]ijk[mn]op => "mn" (letters from the second shelter survive, there is no # close)
#ab#de[fgh]ijk[mn]op => "mn" (letters from the second shelter survive, there is no # close)
#abde[fgh]i#jk[mn]op => "mn" (letters from the second shelter survive, there is only 1 # close)
[a]#[b]#[c]  => "ac"
[a]#b#[c][d] => "d"
[a][b][c]    => "abc"
##a[a]b[c]#  => "c"
```

题意：

```
题目意思就是：
[a]#[b]#[c]  => "ac"

#号代表炸弹，[]代表保护门，如果一对门[]附近的‘#’之和大于等于2，则这扇门就会被炸掉包括[]里面的元素;
如果没有就保留所有的元素；
```

思路：

```
思路就是：
考虑两种情况：
1：没有一个‘#’号
2：有‘#’号就计算‘[]’号两边的#号个数 
```

代码如下：

 由于写的过程不断修改因此代码比较冗余；不够精简

```
def alphabet_war(battlefield):
    string1=""
    list1=[]
    list2=[]
    string2=""
    string3=""
    a=0

    if battlefield.find('#') == -1:
        for x in battlefield:
            if x != '[' and x != ']':
                string3=string3+x
        return string3

    for i in range(0,len(battlefield)):
        if battlefield[i]=='[':
            list1.append(a)
            #print(1)
        if battlefield[i]=='#':
            a=a+1
            #print(2)
        if battlefield[i]==']':
            a=0
            #print(3)
        if i==len(battlefield)-1:
            list1.append(a)
        #print(list1)
    #------
    for i in range(0,len(battlefield)):
        if battlefield[i]=='[':
            for j in range(i+1,len(battlefield)):
                if battlefield[j]==']':
                    list2.append(string1)
                    string1=""
                    break
                else:
                    string1=string1+battlefield[j]
            #print(list2)        
    #---------
    j=0
    for i in range(0,len(list1)-1):
        c=list1[i]+list1[i+1]
        if c < 2:
            string2=string2+list2[j]
        j=j+1
    return string2
```

 看看大神的吧：

```
import re
def alphabet_war(b):
    if '#' not in b:
        return re.sub(r"[\[\]]","",b)
    p = re.compile('([a-z#]*)\[([a-z]+)\](?=([a-z#]*))')
    return  ''.join( e[1] if (e[0]+e[2]).count('#') < 2 else'' for e in p.findall(b))
```

大神用的正则表达式：原来正则表达式就是这么用：re.sub(r"[\你想要去掉的字符]")

+ 代表至少一个

* 代表0-n个

？代表对？前面的RE进行0或1个重复

(?=...)代表 例如, `Isaac(?=Asimov)` 只有跟随着'Asimov'才会匹配'Isaac'。

```
/(\w)((?=111)(1))+/.test("1111") // true
/(\w)((?=111)(1))+/.test("2222") // false
```

```
/(\w)(?=\1{3,})/.test("AAAAAAAA") //true
/(\w)(?=\1{3,})/.test("AAAB") //false
```

## **关于compile()：**

对于re.compile()则是用于编译正则表达式，生成一个正则表达式（ Pattern ）对象，其他函数使用。

```
group([group1, …]) 方法用于获得一个或多个分组匹配的字符串，当要获得整个匹配的子串时，可直接使用 group() 或 group(0)；
start([group]) 方法用于获取分组匹配的子串在整个字符串中的起始位置（子串第一个字符的索引），参数默认值为 0；
end([group]) 方法用于获取分组匹配的子串在整个字符串中的结束位置（子串最后一个字符的索引+1），参数默认值为 0；
span([group]) 方法返回 (start(group), end(group))。
```

```
>>>import re
>>> pattern = re.compile(r'\d+')                    # 用于匹配至少一个数字
>>> m = pattern.match('one12twothree34four')        # 查找头部，没有匹配
>>> print m
None
>>> m = pattern.match('one12twothree34four', 2, 10) # 从'e'的位置开始匹配，没有匹配
>>> print m
None
>>> m = pattern.match('one12twothree34four', 3, 10) # 从'1'的位置开始匹配，正好匹配
>>> print m                                         # 返回一个 Match 对象
<_sre.SRE_Match object at 0x10a42aac0>
>>> m.group(0)   # 可省略 0
'12'
>>> m.start(0)   # 可省略 0
3
>>> m.end(0)     # 可省略 0
5
>>> m.span(0)    # 可省略 0
(3, 5)
```

## 关于findall() :

在字符串中找到正则表达式所匹配的所有子串，并返回一个列表，如果没有找到匹配的，则返回空列表。

```
# -*- coding:UTF8 -*-

import re

pattern = re.compile(r'\d+')   # 查找数字
result1 = pattern.findall('runoob 123 google 456')
result2 = pattern.findall('run88oob123google456', 0, 10)

print(result1)
print(result2)
```

输出： 

```
['123', '456']
['88', '12']
```