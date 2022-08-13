<!--yml
category: codewars
date: 2022-08-13 11:43:43
-->

# 小白的自我救赎：今日份codewars_拾壹�的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixingbiandui/article/details/104596997?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-104596997.nonecase](https://blog.csdn.net/weixingbiandui/article/details/104596997?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-104596997.nonecase)

**题目：**
You are going to be given an array of integers. Your job is to take that array and find an index N where the sum of the integers to the left of N is equal to the sum of the integers to the right of N. If there is no index that would make this happen, return -1.For example:Let’s say you are given the array {1,2,3,4,3,2,1}:Your function will return the index 3, because at the 3rd position of the array, the sum of left side of the index ({1,2,3}) and the sum of the right side of the index ({3,2,1}) both equal 6.Let’s look at another one.You are given the array {1,100,50,-51,1,1}:Your function will return the index 1, because at the 1st position of the array, the sum of left side of the index ({1}) and the sum of the right side of the index ({50,-51,1,1}) both equal 1.Last one:You are given the array {20,10,-80,10,10,15,35}At index 0 the left side is {}The right side is {10,-80,10,10,15,35}They both are equal to 0 when added. (Empty arrays are equal to 0 in this problem)Index 0 is the place where the left side and right side are equal.Note: Please remember that in most programming/scripting languages the index of an array starts at 0.

我的解法：

```
def find_even_index(list1):
    l = len(list1)
    for i in range(l):
        left=list1[0:i]
        right=list1[i+1:l]
        l_num = 0
        r_num = 0
        for x in left:
            l_num += x
        for y in right:
            r_num += y
        if l_num == r_num:
            return i
    return -1
```

大神解法：

```
def find_even_index(arr):
	for i in range(len(arr)):
		if sum(arr[:i]) == sum(arr[i+1:]):
			return i
	return -1 
```

思路是一样的就是我写的太复杂了…哎

**题目：**
In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.

我的代码：

```
def filter_list(l):
  output = []
  s =[x for x in range(1000)]
  for i in l:
      if i in s:
          output.append(i)
  return output
```

投机取巧了= =

还是看看大佬们的吧

```
def filter_list(l):
	output = []
	for i in l :
		if type(i) != str:
			output.append(i)
	return output
```

还有更简单的：

```
def filter_list(l):
	return [i for i in l if not isinstance(i,str)]
```

isinstance(): 如果对象的类型与参数二的类型相同则返回 True，否则返回 False

我好菜…

**题目：**
Given two arrays a and b write a function comp(a, b) (compSame(a, b) in Clojure) that checks whether the two arrays have the “same” elements, with the same multiplicities. “Same” means, here, that the elements in b are the elements in asquared, regardless of the order.ExamplesValid arraysa = [121, 144, 19, 161, 19, 144, 19, 11]
就是在不考虑列表中元素的顺序的前提下判断两个列表中的元素是不是平方的关系

我的代码依旧复杂：

```
import math
def comp(array1, array2):
    output = []
    temp = []
    a1 = array1
    a2 = array2
    for x in a2:
        temp.append(math.sqrt(x))
    for i in a1:
        if i in temp:
            output.append(i)
    if len(output) == len(a2):
        return True
    else:
        return False 
```

大神代码：

```
def cmp(arr1,arr2):
	try:
		return sorted([i**2 for i in arr1]) == sorted(arr2)
	except:
		return False
```

平方后排序看看两个列表是不是完全相同即可 跪拜

**题目：**
The new “Avengers” movie has just been released! There are a lot of people at the cinema box office standing in a huge line. Each of them has a single 100, 50 or 25 dollar bill. An “Avengers” ticket costs 25 dollars.
Vasya is currently working as a clerk. He wants to sell a ticket to every single person in this line.
Can Vasya sell a ticket to every person and give change if he initially has no money and sells the tickets strictly in the order people queue?
Return YES, if Vasya can sell a ticket to every person and give change with the bills he has at hand at that moment. Otherwise return NO.
卖票，一张票25块钱，最开始收银员手里一分都没有（没钱你当什么收银员），问你能不能顺利地把票卖给这些人？

分析：最开始想暴力穷举，但是情况实在是太复杂了这得多暴力才能举出来，然后看了网上的代码…

```
def tickets(people):
	change = {25 : 0,50 : 0}
	for money in people:
		if money == 25:
			change[25] += 1
		elif money == 50:
			change[50] += 1
			change[25] -= 1
		else:
			if change[50] > 1:
				change[50] -= 1
				change[25] -=1
			else:
				change[25] -=3
		if change[25] < 0 or change[50] <0 :
			return 'NO'
	return 'YES'
```

**题目：**
You might know some pretty large perfect squares. But what about the NEXT one?
Complete the findNextSquare method that finds the next integral perfect square after the one passed as a parameter. Recall that an integral perfect square is an integer n such that sqrt(n) is also an integer.
If the parameter is itself not a perfect square, than -1 should be returned. You may assume the parameter is positive.

就是判断一个数字是不是完全平方数，如果是的话就返回这个完全平方数的下一个完全平方数，否则返回-1

最开始的思路：只需要判断开方之后的数字是否为整型即可，所以最开始的思路是：

```
def find_next_square(sq):
	if (type(sq**0.5)) == int:
		return (((sq**0.5)+1)**2)
	else:
		return -1
```

但是！！！这种方法返回的都是-1，因为开方之后的结果都是浮点型！！！

因此可以稍微转换一下：

```
def find_next_square(sq):
	a = sq ** 0.5
	b = int(a)
	if a == b:
		return ((b+1)**2)
	else:
		return -1
```

再看看别人的：

```
import math
def find_next_square(sq):
	if (math.sqrt(sq)) == math.trunc(math.sqrt(sq)):
		return (math.sqrt(sq)+1)**2
	else:
		return -1
```

区别只在于我们是用int强制转换之后对比
这里面的trunc()方法的作用是直接舍弃小数部分

更精简的版本：

```
def find_next_square(sq):
	sq = sq ** 0.5
	if sq.is_integer():
		return (sq + 1)**2
	else:
		return -1
```

核心思想就是判断开方之后的数是不是整数