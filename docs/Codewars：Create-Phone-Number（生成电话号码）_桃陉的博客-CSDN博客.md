<!--yml
category: codewars
date: 2022-08-13 11:38:00
-->

# Codewars：Create Phone Number（生成电话号码）_桃陉的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_46308081/article/details/119357194?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-13-119357194-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_46308081/article/details/119357194?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-13-119357194-null-null.142^v40^control,185^v2^control&utm_term=codewars)

* * *

## 写在前面

这个题实际上非常简单，就是拼接生成字符串，但是我做完以后发现别人的一种做法，我大受震撼，感觉很巧妙，这种思想说不定以后也用得到，就摘出来做个纪念哇！

* * *

## 1.问题描述

`原题`：

∙ \bullet ∙ Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.

∙ \bullet ∙ Example:

> createPhoneNumber(int[10]{1, 2, 3, 4, 5, 6, 7, 8, 9, 0}) // => returns “(123) 456-7890”

难 度 ： 6 k y u {\color{Purple} 难度：6kyu} 难度：6kyu

* * *

`翻译`：

∙ \bullet ∙ 编写一个函数，接受一个由10个整数(介于0和9之间)组成的数组，该数组以电话号码的形式返回这些数字的字符串。

* * *

## 2.分析

∙ \bullet ∙ 这是一道简单的数字转字符然后按照指定规则生成字符串的题目。

∙ \bullet ∙ 按照一般人的思路肯定是循环一遍，遇到特殊的位置，标记出来然后插入指定字符，形成最后答案。

∙ \bullet ∙ 但是还可以先生成一个带有目标格式的字符串，比如这里就可以写成 s t r i n g   r e s = “ ( . . . ) . . . − . . . . " string \ res = “(...) ...-...." string res=“(...)...−...."，就是先将需要特殊填入的字符写入，然后其他位置使用 . . .来进行占位，最后只需要填入这些数据即可。

* * *

## 3.代码

∙ \bullet ∙ `一般代码`：

```
string createPhoneNumber(const int arr [10]){
    string res="(";
    for(int i=0;i<10;i++)
    {
    	if(i==3) res+=") ";
    	if(i==6) res+='-';
    	res += arr[i]+'0';
    }
    return res;
} 
```

∙ \bullet ∙ `格式化处理的代码`：

```
string createPhoneNumber(const int digits[10]) {
	string res = "(...) ...-....";
	for (unsigned is = 0, id = 0; is < res.length(); is++)
	    if (res[is] == '.')
	        res[is] = '0' + digits[id++];
	return res;
} 
```