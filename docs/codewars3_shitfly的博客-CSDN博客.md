<!--yml
category: codewars
date: 2022-08-13 11:42:47
-->

# codewars3_shitfly的博客-CSDN博客

> 来源：[https://blog.csdn.net/s969966195/article/details/71424597?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-24-71424597-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/s969966195/article/details/71424597?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-24-71424597-null-null.142^v40^control,185^v2^control&utm_term=codewars)

**Where my anagrams at?**

```
def anagrams(word,words):
    lword=list(word)
    lword.sort()
    new=[]
    for i in range(len(words)):
        lwords=list(words[i])
        lwords.sort()
        if lword==lwords:
            new.append(words[i])
    return new
```

将排好序的字符串和列表中的排好序的字符串做比较。
**Twice linear**

```
def dbl_linear(n):
    x=1
    l=list()
    l.append(x)
    y,z=0,0
    yi,zi=0,0
    l1=[]
    while len(l)<n+1:
        y=2*l[yi]+1
        z=3*l[zi]+1
        lenth=len(l)
        if y>z:
            if l[lenth-1]!=z:
                l.append(z)
            zi+=1
        else:
            if l[lenth-1]!=y:
                l.append(y)
            yi+=1
    return l[n]
```

上一个版本忘了存，答案虽然对，但是效率很低。这个答案借鉴了[CodeWars Twice linear 算法问题](http://bbs.csdn.net/topics/391927111)。
只要有涉及到数组元素查找、数组元素排序，n值一大必然会导致性能差。
1、既然产生数值（2x+1 或 3x+1）必须以升序数组元素值为基础，那么可以考虑push数组时就是有序的
2、每次循环只需要把（2yi + 1）、(3zi+1)中较小值给数组即可。而yi和zi分别产生此次较小值的数组index，每产生一个较小值对应数组index就加1即可。
3、只需要让数组长度<=n+1即可取的所需值

看别人的答案，发现了collections中的deque，用队列来做

```
from collections import deque

def dbl_linear(n):
    u, q2, q3 = 1, deque([]), deque([])
    for _ in range(n):
        q2.append(2 * u + 1)
        q3.append(3 * u + 1)
        u = min(q2[0], q3[0])
        if u == q2[0]: q2.popleft()
        if u == q3[0]: q3.popleft()
    return u
```

两个队列来做。

**Base Conversion**

```
 bin='01'
oct='01234567'
dec='0123456789'
hex='0123456789abcdef'
allow='abcdefghijklmnopqrstuvwxyz'
allup='ABCDEFGHIJKLMNOPQRSTUVWXYZ'
alpha='abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
alphanum='0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'

def convert(input, source, target):
    source=list(source)
    target=list(target)
    hs={}
    ls=len(source)
    lt=len(target)
    for i in range(ls):
        hs[source[i]]=i
    n=0
    for j in input:
        n=n*ls+hs[j] 
    res=[]
    while n>0:
        res.append(target[n%lt])
        n/=lt
    if len(res)==0:
        res.append(target[0])
    return ''.join(res[::-1])
```

一开始题目没看懂，比如不知道allow怎么转化到hex。因为输入的都是字符串，其实就是字符串按照源字母的进制得出的数字再按目标字母转化。
可以不用字典，使用str.index()返回某个值第一个匹配项的索引位置

```
n=n*ls+source.index(j)
```

**Roman Numerals Decoder**

```
def solution(roman):
    d={'M':1000,
        'D':500,
        'C':100,
        'L':50,
        'X':10,
        'V':5,
        'I':1
    }
    ans=0
    i=0
    while i<len(roman):
        if i<len(roman)-1 and d[roman[i+1]]>d[roman[i]]:
            ans+=d[roman[i+1]]-d[roman[i]]
            i+=2
        else:    
            ans+=d[roman[i]]
            i+=1
    return ans
```

这题比较简单，学习了一个内建函数zip()，它接受一系列可迭代的对象作为参数，将对象中对应的元素打包成一个个tuple（元组），然后返回由这些tuples组成的list（列表）。

```
_rdecode = dict(zip('MDCLXVI', (1000, 500, 100, 50, 10, 5, 1)))

def decode( roman ):
    result = 0
    for r, r1 in zip(roman, roman[1:]):
        rd, rd1 = _rdecode[r], _rdecode[r1]
        result += -rd if rd < rd1 else rd
    return result + _rdecode[roman[-1]]
```