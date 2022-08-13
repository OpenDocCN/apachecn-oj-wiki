<!--yml
category: codewars
date: 2022-08-13 11:40:47
-->

# 【Codewars python 5kyu】: First non-repeating character_小菜鸟快飞的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36362028/article/details/100547419?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-29-100547419-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_36362028/article/details/100547419?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-29-100547419-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 问题描述：

Write a function named `first_non_repeating_letter` that takes a string input, and returns the first character that is not repeated anywhere in the string.

For example, if given the input `'stress'`, the function should return `'t'`, since the letter *t* only occurs once in the string, and occurs first in the string.

As an added challenge, upper- and lowercase letters are considered the **same character**, but the function should return the correct case for the initial letter. For example, the input `'sTreSS'`should return `'T'`.

If a string contains *all repeating characters*, it should return an empty string (`""`) or `None` -- see sample tests.

# 代码实现：

```
#codewars第十二题
def first_non_repeating_letter(string):
    #your code here
    my_str = string.upper()
    ss = list(my_str)
    _length = len(ss)
    for i in range(0,_length):
        if ss.count(ss[i]) == 1:    #count()统计list中出现指定字符的次数
            return string[i]
        else:
            continue
    return ''

#另解
def first_non_repeating_letter(string):
    string_lower = string.lower()
    for i, letter in enumerate(string_lower):
        print(letter)
        print(i)
        if string_lower.count(letter) == 1:
            return string[i]

    return ""

first_non_repeating_letter('Go hang a salami, I\'m a lasagna hog!')
```