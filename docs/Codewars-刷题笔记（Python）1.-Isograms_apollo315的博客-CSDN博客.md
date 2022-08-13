<!--yml
category: codewars
date: 2022-08-13 11:41:43
-->

# Codewars 刷题笔记（Python）1\. Isograms_apollo315的博客-CSDN博客

> 来源：[https://blog.csdn.net/apollo315/article/details/104603841?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-21-104603841-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/apollo315/article/details/104603841?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-21-104603841-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## 题目

An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore letter case.

```
is_isogram("Dermatoglyphics" ) == true
is_isogram("aba" ) == false
is_isogram("moOse" ) == false 
```

> 难度：7 kyu

## 我的解法

```
def is_isogram(string):

    string = string.lower()
    string_set = []
    for alphabet in string:
        if alphabet not in string_set:
            string_set.append(alphabet)
        else:
            pass
    if list(string) == string_set:
        return True
    else:
        return False 
```

思路也比较简单：

1.  因为题目要求是忽略字母大小写来对比，所以我开始对传入的字符串做了统一小写的处理`string.lower()`
2.  然后我设置了一个列表，来筛选字符串，只保留不重复的字母
3.  最后将这个列表和字符串做一个对比，如果完全一致，则说明字符串中的字母都是不重复的，那么就返回`True`，如果不一致，则说明字符串中有重复字母，所以返回False。

## 更优解法

```
def is_isogram(string):
    return len(string) == len(set(string.lower())) 
```

一行代码就实现了要求的功能，而且看起来简洁易懂

## 学习总结

1.  去重我想到了，对比长度实在是没想到，这个方法更加简单。
2.  整体思路相近，但是实现的代码差距很大，别人1行代码实现了我10+行的功能。
3.  集合（set）是去重的最高效的方法
4.  序列（字符串、列表等）和集合（set）都可以用内置函数`len`来查询长度。