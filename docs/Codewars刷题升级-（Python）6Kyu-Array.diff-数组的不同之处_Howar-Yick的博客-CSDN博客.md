<!--yml
category: codewars
date: 2022-08-13 11:41:15
-->

# Codewars刷题升级 （Python）6Kyu Array.diff 数组的不同之处_Howar Yick的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41432655/article/details/93790560?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-8-93790560-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_41432655/article/details/93790560?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-8-93790560-null-null.142^v40^control,185^v2^control&utm_term=codewars)

**题目描述：**

> Your goal in this kata is to implement a difference function, which subtracts one list from another and returns the result.
> 此训练的目的是制定一个差别函数，用一个列表减去另一个列表，并返回结果。

> It should remove all values from list a, which are present in list b.
> 它应该从列表a中删除所有出现在列表b中的值。

```
array_diff([1,2],[1]) == [2] 
```

> If a value is present in b, all of its occurrences must be removed from the other:
> 如果一个值在b中出现，所有在a中出现的这个值都要删除。

```
array_diff([1,2,2,2,3],[2]) == [1,3] 
```

**解题思路：**
用列表推导式很容易是实现这个函数

**代码实现：**

```
def array_diff(a, b):
    #your code here
    return [x for x in a if x not in b] 
```