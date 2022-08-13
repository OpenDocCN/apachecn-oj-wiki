<!--yml
category: codewars
date: 2022-08-13 11:43:13
-->

# 2019/9/28_codewars自虐_输出单词的中间字母_LLlllkw的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36512834/article/details/101638464?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-101638464.nonecase](https://blog.csdn.net/qq_36512834/article/details/101638464?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-101638464.nonecase)

**题目原文：**You are going to be given a word. Your job is to return the middle character of the word. If the word’s length is odd, return the middle character. If the word’s length is even, return the middle 2 characters.

#Examples:

Kata.getMiddle(“test”) should return “es”

Kata.getMiddle(“testing”) should return “t”

Kata.getMiddle(“middle”) should return “dd”

Kata.getMiddle(“A”) should return “A”
#Input

A word (string) of length 0 < str < 1000 (In javascript you may get slightly more than 1000 in some test cases due to an error in the test cases). You do not need to test for this. This is only here to tell you that you do not need to worry about your solution timing out.

#Output

The middle character(s) of the word represented as a string.

**感觉这道题比较简单，直接先读取字符串长度，然后分为奇数偶数讨论，直接用字符串的索引方式输出即可
给出自己写的最简单最清晰的代码：

```
def get_middle(s):
    	length=len(s)
    	print(length)
    	if length%2==0:
        	return(s[int(length/2-1)]+s[int(length/2)])
get_middle("smooth")** 
```

这里要注意的是Python和C语言不同，Python可以直接使用len（string）方法获得字符串长度，并且可以用类似于索引的方式输出字符串的第几个字符（一个字符对应一个索引），这一点比C语言方便很多
**另外要注意**：Python的字符串索引一定要是整数，这里length/2以后int直接被转换成了float，所以一直报错，要用int（）进行强制转换