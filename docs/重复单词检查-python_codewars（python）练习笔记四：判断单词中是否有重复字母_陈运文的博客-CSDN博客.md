<!--yml
category: codewars
date: 2022-08-13 11:40:28
-->

# 重复单词检查 python_codewars（python）练习笔记四：判断单词中是否有重复字母_陈运文的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_32019909/article/details/112961737?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-19-112961737-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_32019909/article/details/112961737?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-19-112961737-null-null.142^v40^control,185^v2^control&utm_term=codewars)

codewars(python)练习笔记四：判断单词中是否有重复字母(不区分大小写)

题目：

An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore letter case.

test case：

is_isogram("Dermatoglyphics" ) == true

is_isogram("aba" ) == false

is_isogram("moOse" ) == false # -- ignore letter case

题目大意：

找出字符串中的重复字母，不区分大小写。

我的解法：

def is_isogram(string):

temp_list = []

for item in list(string):

item = item.lower()

if item in temp_list:

return False

else:

temp_list.append(item)

return True

牛逼一点的解法：

def is_isogram(string):

s = set(string.lower())

if len(s) == len(string):

return True

return False

这个就是对set的运用。

优化：

def is_isogram(string):

return len(string) == len(set(string.lower()))