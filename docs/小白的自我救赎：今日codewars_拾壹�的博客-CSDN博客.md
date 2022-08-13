<!--yml
category: codewars
date: 2022-08-13 11:34:35
-->

# 小白的自我救赎：今日codewars_拾壹�的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixingbiandui/article/details/104650878?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-104650878.142^v40^control,185^v2^control](https://blog.csdn.net/weixingbiandui/article/details/104650878?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-104650878.142^v40^control,185^v2^control)

**题目：**
Complete the function scramble(str1, str2) that returns true if a portion of str1 characters can be rearranged to match str2, otherwise returns false.
Notes:

Only lower case letters will be used (a-z). No punctuation or digits will be included.
Performance needs to be considered
就是给我们两个字符串让我们判断由s1中的字符能不能组成s2中的字符

代码：

```
def scramble(s1, s2):
    if len(s1) < len(s2):
        return False
    else:
        for i in s2:
            if s2.count(i) > s1.count(i):
                return False
        return True
```

可以通过但是attempt就会提示我超时，让我优化代码…试了很多方法都做不到把时间变短，无奈放弃
看了一眼答案

```
def scramble(s1,s2):
    for c in set(s2):
        if s1.count(c) < s2.count(c):
            return False
    return True
```

在遍历查找之前把s2写成了一个集合，这样就不会重复查找同样的元素了，行吧我还能说什么呢 = =

You have an array of numbers.
Your task is to sort ascending odd numbers but even numbers must be on their places.
Zero isn’t an odd number and you don’t need to move it. If you have an empty array, you need to return it.

Example
sort_array([5, 3, 2, 8, 1, 4]) == [1, 3, 2, 8, 5, 4]

要求根据给出的列表，把列表中的奇数排序，偶数位置不变

分析：显然我们可以先把列表中的奇数元素找出来组成一个新列表并排序，然后再根据列表中偶数元素的位置将偶数插入到新列表中

```
def sort_array(source_array):
	newlist = []
	for i in source_array:
		if i % 2 == 1:
			newlist.append(i)
	newlist.sort()
	for j in range(len(source_array)):
		if source_array[j] % 2 == 0:
			newlist.insert(j,source_array[j])
	return newlist
```

高亮代码：

```
def sort_array(arr):
  odds = sorted((x for x in arr if x%2 != 0), reverse=True)
  return [x if x%2==0 else odds.pop() for x in arr]
```

**题目：**

Pete likes to bake some cakes. He has some recipes and ingredients. Unfortunately he is not good in maths. Can you help him to find out, how many cakes he could bake considering his recipes?
Write a function cakes(), which takes the recipe (object) and the available ingredients (also an object) and returns the maximum number of cakes Pete can bake (integer). For simplicity there are no units for the amounts (e.g. 1 lb of flour or 200 g of sugar are simply 1 or 200). Ingredients that are not present in the objects, can be considered as 0.

就是给我们两个字典，分别存储着原材料的量与做成这个食材需要的量，问我们最多能做出几个成品

分析：
首先，当原材料的种类少于需要材料的种类时，肯定不能做出来。
然后我们可以照着需求把原材料中对应的材料取出来组成一个新的字典，然后比对数量即可

```
def cakes(recipe,available):
	if len(recipe) > len(available):
		return 0
	else:
		dic = {}
		number = []
		for key in recipe:
			dic[key] = available[key]
		for key in dic:
			number.append(dic[key] // recipe[key])
		return min(number)
```

高亮代码：

```
def cakes(recipe, available):
  return min(available.get(k, 0)/recipe[k] for k in recipe)
```

行吧…我写那么复杂结果人家一句话就解决了
get()函数：dict.get(key, default=None)
返回指定键的值，如果值不在字典中返回默认值
key – 字典中要查找的键。
default – 如果指定键的值不存在时，返回该默认值。