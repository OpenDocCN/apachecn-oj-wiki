<!--yml
category: codewars
date: 2022-08-13 11:44:59
-->

# codewars遇到的比较有意思的题目_卖女孩的小火柴2号的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_31129899/article/details/53239349?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-53239349.nonecase](https://blog.csdn.net/qq_31129899/article/details/53239349?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-53239349.nonecase)

题目要求是编写一个函数用来检测一个字符串，字符串是一系列单词组成，每个单词间用空格隔开，不用考虑空字符串的情况，返回长度最小的那个单词的长度。

博主刚入门php，技术还很菜，没有想出来，看了其他人的解决方案，最简洁的方案是

```
function findShort($str){
   return min(array_map('strlen', (explode(' ', $str))));
}
```

explode()是把字符串打散成索引数组，意思是每个单词都成了数组的一个键值，array_map()是指将用户自定义函数作用到数组中的每个值上，并返回用户自定义函数作用后的带有新值的数组，strlen是php自带的一个函数，返回字符串长度，这样到array_map()函数这一层，就返回了每个单词的长度组成的一个索引数组。

min() 返回参数中数值最小的。如果仅有一个参数且为数组，min() 返回该数组中最小的值。这样就ruturn了长度最小的那个单词的长度。