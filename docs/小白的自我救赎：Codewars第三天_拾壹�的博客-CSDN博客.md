<!--yml
category: codewars
date: 2022-08-13 11:28:00
-->

# 小白的自我救赎：Codewars第三天_拾壹�的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixingbiandui/article/details/104559395?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-104559395.142^v40^control,185^v2^control](https://blog.csdn.net/weixingbiandui/article/details/104559395?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-104559395.142^v40^control,185^v2^control)

**题目：**
An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore letter case.
就是不区分字符串中字母大小写的情况下判断字符串中有没有重复的字母

我的代码：

```
def is_isogram(string):
    string=string.lower()
    if len(string) == 0:
        return True
    else:
        newstring=list(string)
        for i in range(len(newstring)-1):
            for j in range(i+1,len(newstring)):
                if newstring[i] == newstring[j]:
                    return False
        return True 
```

哎 简直太复杂了
看看别人的代码

```
def is_isogram(string):
    temp_list = []
    for item in list(string):
        item = item.lower()
        if item in temp_list:
            return False
        else:
            temp_list.append(item)
    return True 
```

还有更厉害的

```
def is_isogram(string):
    s = set(string.lower()) 
    if len(s) == len(string): 
        return True
    return False 
```

灵活运用集合

**题目:**
Write a function that will return the count of distinct case-insensitive alphabetic characters and numeric digits that occur more than once in the input string. The input string can be assumed to contain only alphabets (both uppercase and lowercase) and numeric digits.
统计字符串中有几个单词有重复，不必考虑大小写

分析：
已经说了不考虑大小写，那么先全部小写。
统计重复单词的个数：把有重复的单词扔到列表里最后求列表的长度就知道有几个重复的单词了

```
def duplicate_count(text):
	string = text.lower()
	output = []
	for i in string:
		if string.count(i)>= 2 and i not in output:
			output.append(i)
	return len(output) 
```