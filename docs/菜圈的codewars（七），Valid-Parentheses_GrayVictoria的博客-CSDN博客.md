<!--yml
category: codewars
date: 2022-08-13 11:49:28
-->

# 菜圈的codewars（七），Valid Parentheses_GrayVictoria的博客-CSDN博客

> 来源：[https://blog.csdn.net/GrayVictoria/article/details/51332471?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-51332471.nonecase](https://blog.csdn.net/GrayVictoria/article/details/51332471?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-51332471.nonecase)

这道题是找一个字符串中的括号是不是都是成对的，如果是返回true，否则返回false

其实都是acm入门题的难度，换个语言写熟练熟练

我的比较麻烦了，看到一个左括号，从后面找右括号，有的话就把他俩一起排除，如果最后还剩括号的话就是不成对的

```
def valid_parentheses(string):
	string=list(string)
	i=0
	while i<len(string):
		if string[i]=='(' :
			j=i
			flag=0
			while j<len(string):
				if string[j]==')':
					string[i]='0'
					string[j]='0'
					flag=1
					break
				j+=1
			if flag==0 :
				return False
		i=i+1
	i=0
	while i<len(string):
		if string[i]=='(' or string[i]==')':
			return False
		i+=1
	return True
```

麻烦的一比……

另附大神代码，这个代码堆得太好了，就是拐个弯的事，看我搞得多复杂……

唉……都是码农差距这么大

```
def valid_parentheses(string):
    cnt = 0
    for char in string:
        if char == '(': cnt += 1
        if char == ')': cnt -= 1
        if cnt < 0: return False
    return True if cnt == 0 else False
```