<!--yml
category: codewars
date: 2022-08-13 11:44:25
-->

# codeWars之-查找缺少的字母_Vai歪的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_37890936/article/details/78566427?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-78566427.nonecase](https://blog.csdn.net/weixin_37890936/article/details/78566427?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-78566427.nonecase)

在日常刷题的过程中，总有过不了的题，就像这道题，自己的代码Load times过久过不了，附上题目和最佳答案记录一下这条相对经典的题吧。

题目大概是这样的：

Write a method that takes an array of consecutive (increasing) letters as input and that returns the missing letter in the array.

You will always get an valid array. And it will be always exactly one letter be missing. The length of the array will always be at least 2.
The array will always contain letters in only one case.

Example:

['a','b','c','d','f'] -> 'e'
['O','Q','R','S'] -> 'P'

function findMissingLetter(array) {

var string = array.join("");

for (var i = 0; i < string.length; i++) {

if (string.

charCodeAt

(i + 1) - string.charCodeAt(i) != 1) {

return

String.fromCharCode

(string.charCodeAt(i) + 1);

}

}

}

这道题最主要的是他利用了Unicode码在相邻字母相差1的特点直接就算出那个缺少的字母，而不是我原来还要用一个数组记录24字母再去匹配，这个才是一个值得我学习的点。希望你们看到也能和我有收获。虽然挺简单的，可还是记录下来比较好，毕竟自己的基础和算法有待提高。

再总结下这几天下来用过的方法，splice(),filter(fun(x)),replace();substring(),reduce(fun(c,y),0)