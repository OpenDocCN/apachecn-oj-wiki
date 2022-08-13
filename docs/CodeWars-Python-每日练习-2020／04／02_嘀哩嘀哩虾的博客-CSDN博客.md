<!--yml
category: codewars
date: 2022-08-13 11:51:23
-->

# CodeWars-Python 每日练习-2020/04/02_嘀哩嘀哩虾的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42945953/article/details/105279919?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-105279919.nonecase](https://blog.csdn.net/weixin_42945953/article/details/105279919?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-105279919.nonecase)

题目：

```
Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.

Example:
create_phone_number([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]) 
```

思路1：replace方法

```
def create_phone_number(n):
	phone = '(xxx) xxx-xxxx'
	for each in n:
		phone = phone.replace('x', str(each), 1)
	return phone 
```

语法：
str.replace(old, new[,max])
说明： 使用new替换new 字符串, 参数max可选，设置表示最大替换次数
max为1，即表示最大替换1次。
for each in n:
列表元素为整形int， 转化为str

思路2：format() 方法和 map()方法

```
def create_phone_number(n):

    n = ''.join(map(str, n))
    return "({}) {}-{}".format(n[:3], n[3:6], n[6:10]) 
```

错误使用

```
>>> ''.join(i for i in n)   
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: sequence item 0: expected str instance, int found
类型错误： 序列0，期望实例str,找到int
''.join(str(i) for i in n) 
```

# 创建一个迭代器，使用str方法计算每个迭代产生的参数 map(str,n)

# 将map object转化为list，参数必须是一个迭代器 iterable

list(map(str,n))