<!--yml
category: codewars
date: 2022-08-13 11:41:58
-->

# Codewars--How many numbers III? （python）_静看丶雨落时的博客-CSDN博客

> 来源：[https://blog.csdn.net/xiaopc3357/article/details/81291579?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-29-81291579-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/xiaopc3357/article/details/81291579?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-29-81291579-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## How many numbers III?

**难度系数 4kyu**

这题目一开始没看懂什么意思，但感觉应该是个挺有意思的题目就直接跳过查看答案，看完答案才明白题目的意思，本题引用 **yojimboz的答案，[https://www.codewars.com/users/yojimboz](https://www.codewars.com/users/yojimboz)** 。

**题目的意思大概是输入两个数，第一个为数字之和，第2个为由n位数组成，输出为有多少个这样的n位数，最小值是多少，最大值是多少。**

**题目：**
We want to generate all the numbers of three digits that:
the value of adding their corresponding ones(digits) is equal to 10\.
their digits are in increasing order (the numbers may have two or more equal contiguous digits)
The numbers that fulfill the two above constraints are: 118, 127, 136, 145, 226, 235, 244, 334
Make a function that receives two arguments:
the sum of digits value
the amount of desired digits for the numbers
**The function should output an array with three values: [1,2,3]**
**1 - the total amount of all these possible numbers**
**2 - the minimum number**
**3 - the maximum numberwith**

**The example given above should be:**

> find_all(10, 3) == [8, 118, 334]
> If we have only one possible number as a solution, it should output a result like the one below:
> 
> find_all(27, 3) == [1, 999, 999]
> If there are no possible numbers, the function should output the empty array.
> 
> find_all(84, 4) == []
> The number of solutions climbs up when the number of digits increases.
> 
> find_all(35, 6) == [123, 116999, 566666]

代码：
主要采用系统自带的itertools工具包中的`combinations_with_replacement` 函数，它可以十分方便的遍历这n位数，如果数字和等于给定值则保存！ **对就是这么简单！不看不知道，一看发现自己懂得太少！！**

```
from itertools import combinations_with_replacement

def find_all(sum_dig, digs):
    combs = combinations_with_replacement(list(range(1, 10)), digs) 
    target = [''.join(str(x) for x in list(comb)) for comb in combs if sum(comb) == sum_dig]
    if not target:
        return []
    return [len(target), int(target[0]), int(target[-1])] 
```