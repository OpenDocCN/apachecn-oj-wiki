<!--yml
category: codewars
date: 2022-08-13 11:37:26
-->

# 【Codewars python 4kyu】: Permutations_小菜鸟快飞的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36362028/article/details/100547852?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-2-100547852-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_36362028/article/details/100547852?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-2-100547852-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 问题描述：

In this kata you have to create all permutations of an input string and remove duplicates, if present. This means, you have to shuffle all letters from the input in all possible orders.

Examples:

```
permutations('a'); # ['a']
permutations('ab'); # ['ab', 'ba']
permutations('aabb'); # ['aabb', 'abab', 'abba', 'baab', 'baba', 'bbaa']
```

The order of the permutations doesn't matter.

# 代码实现：

```
#codewars第二十三题
import itertools   #全排列
def permutations(string):
    res = itertools.permutations(string)  #这个方法返回的是一个迭代器  可以用set  list   tuple 转化为相应的格式字符串组 
    return ["".join(str) for str in (set(res))]   #join方法可以将一个组内的用特定符号连接起来  for str in (set(res))  中的str是每一个括号内的

#另解
def permutations(string):
    if len(string) <= 1:
        return string
    else:
        result = []
        for i in range(len(string)):
            for j in permutations(string[0:i] + string[i+1:]):
                result.append(string[i] + j)
        return set(result)

permutations('aabb')
```