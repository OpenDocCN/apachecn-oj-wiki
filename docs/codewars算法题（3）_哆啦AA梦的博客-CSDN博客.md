<!--yml
category: codewars
date: 2022-08-13 11:43:12
-->

# codewars算法题（3）_哆啦AA梦的博客-CSDN博客

> 来源：[https://blog.csdn.net/y1535766478/article/details/76020534?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-76020534.nonecase](https://blog.csdn.net/y1535766478/article/details/76020534?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-76020534.nonecase)

**第三题：**

问题：You probably know the "like" system from Facebook and other pages. People can "like" blog posts, pictures or other items. We want to create the text that should be displayed next to such an item.

Implement a function `likes :: [String] -> String`, which must take in input array, containing the names of people who like an item. It must return the display text as shown in the examples:

自己代码：

def likes(names):
    if(len(names)==0):
        return "no one likes this"
    elif(len(names)==1):
        return names[0]+" likes this"
    elif(len(names)==2):
        return names[0]+" and "+names[1]+" like this"
    elif(len(names)==3):
        return names[0]+", "+names[1]+" and "+names[2]+" like this"
    else:
        return names[0]+", "+names[1]+" and "+str(len(names)-2)+" others like this" 

评分较高代码：

1.  def likes(names):  
2.  n = len(names)  
3.  return {  
4.  0: 'no one likes this',  
5.  1: '{} likes this',   
6.  2: '{} and {} like this',   
7.  3: '{}, {} and {} like this',   
8.  4: '{}, {} and {others} others like this'  
9.  }[min(4, n)].format(*names[:3], others=n-2) 

鹅鹅鹅~~~~~·这就是差距啊

第四题：

问题：

Accumul.accum("abcd"); // "A-Bb-Ccc-Dddd"
Accumul.accum("RqaEzty"); // "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
Accumul.accum("cwAt"); // "C-Ww-Aaa-Tttt"
The parameter of accum is a string which includes only letters from a..z and A..Z.

评分较高代码：

（1）：

 （2）：

（3）：

        其中title()方法返回“标题化”字符串，就是说所有单词都是以大写开始，其余字母均为小写

第五题：（从奇中找偶，从偶中找奇）

问题： You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns N.

 For example:

[2, 4, 0, 100, 4, 11, 2602, 36]

Should return: 11

[160, 3, 1719, 19, 11, 13, -21]

Should return: 160

问题陈述： 目的是一个列表中异类，即列表中大多数为偶数，则返回奇数，否则反之 代码实现：

 (1)      

(2)

第六题：（字符串中是否有重复字符）

问题：An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore letter case.

```
is_isogram("Dermatoglyphics" ) == true
is_isogram("aba" ) == false
is_isogram("moOse" ) == false 
```

代码实现： （1）   

（2）

set()函数，set中参数的值是不能重复的例如：set(“hello”),结果为‘h’‘e’‘l’‘o’

201707242237持续更新~~~~