<!--yml
category: codewars
date: 2022-08-13 11:33:45
-->

# 菜逼的codewars之旅_Devil Coding的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_43315751/article/details/89513925?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-89513925.142^v40^control,185^v2^control](https://blog.csdn.net/weixin_43315751/article/details/89513925?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-89513925.142^v40^control,185^v2^control)

现阶段本人还只是个6kyu，偶尔能写写5kyu这种具有算法的题目，本人主要用python进行编写，，，

如有不妥之处各位大佬还请多多包涵

Reverse Word

问题表述：完成接受字符串参数的函数，并反转字符串中的每个单词。字符串中的所有空格都应保留。

此问题可用python中的split（）方法进行分隔

```
#7 kyu
#tip：Reverse words
def reverse_words(text):
    return ' '.join(a[::-1] for a in text.split(' '))
```

maximum length difference

问题描述:有两个字符串数组a1和a2。每个字符串由字母a到z组成。让x是第一个数组中的任意字符串，y是第二个数组中的任意字符串。

查找最大值（abs（length（x）−length（y）））

如果a1和/或a2为空，则每种语言返回-1，haskell（f）除外，在这里您将不返回任何内容（无）。

```
#7 kyu
#Maximum Length Difference
Python:

def mxdiflg(a1, a2):
    if a1 and a2:
        return max(abs(len(x)-len(y)) for x in a1 for y in a2)
    else:
        return -1
    # your code
```

Kata 2019: Combine Fruits 

问题描述：
约翰是个果园工人。
有N堆水果等待运输。每一堆水果都有相应的重量。约翰的工作是把水果堆成一堆，等卡车把它们运走。
每次，约翰都可以把任何两堆水果（可能是相邻的，也可能不是相邻的）结合起来，他所花费的能量等于两堆水果的重量。
例如，如果有两个桩，Pile1的重量为1，Pile2的重量为2。合并后，新桩的重量为3，他消耗了3单位能量。
约翰想把所有的水果用最少的能量堆成一堆。
你的任务是帮助约翰，计算他花费的最小能量。
输入
水果：正整数的数组。每个元素代表一堆水果的重量。

```
#6 kyu
#Kata 2019: Combine Fruits
#Python:

def comb(fruits):    
    energy=0
    if len(fruits)==1:
        return 0
    while len(fruits)!=1:
        fruits.sort()
        delta = sum(fruits[:2])
        energy += delta
        fruits = [delta] + fruits[2:]
    return energy 
```