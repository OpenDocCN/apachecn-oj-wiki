<!--yml
category: codewars
date: 2022-08-13 11:48:59
-->

# [从codewars学习到的JS系列1]数组方法reduce(),map(),正则$1等的使用_小船划向前端的博客-CSDN博客

> 来源：[https://blog.csdn.net/wayne0902/article/details/51788884?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-51788884.nonecase](https://blog.csdn.net/wayne0902/article/details/51788884?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-51788884.nonecase)

刚开始在codewars上练JS题，从难度最低的8kyu开始。来这里练题写代码不仅是锻炼自己的编程逻辑思维，更是希望自己写完后看别人高效简洁的代码，知道自己还有哪些不足，哪些知识点没掌握，原来遇到这种情况还可以使用这种方法等，从而提高自己代码书写的质量，而不至于自己埋头写代码却没有任何成长，借鉴并模仿学习，最后变成自己的东西！

以下两道题虽简单，自己可能用for循环写完简单了事了，若不是看了其他牛人写的高质量的代码，又怎知还有以下技巧？

* * *

<**level0**>问题：求数组所有项的平均数，向下取整，如输入[2，3，2]，输出2

solution:

```
function getAverage(marks){
  return ~~(marks.reduce((sum, x) => sum + x) / marks.length);
}
```

说明：
1) ~表示位操作符中的按位非，连取两次按位非即可把浮点数向下取整为整数，相当于Math.floor。

2) reduce为数组方法，接收一个函数作为累加器（accumulator），数组中的每个值（从左到右）开始合并，最终为一个值。详细用法见MDN。
应用：将数组所有项相加、数组扁平化

```
var flattened = [[0, 1], [2, 3], [4, 5]].reduce(function(a, b) {
    return a.concat(b);
});
// flattened is [0, 1, 2, 3, 4, 5]
```

返回的是最后一次迭代中previous的值，所以返回的是[0, 1, 2, 3, 4, 5]而不是[[0, 1, 2, 3, 4, 5]]）

3) (sum, x) => sum + x为ES6中的写法，等价于
function (sum,x) { return sum + x };

* * *

<**level0**>问题：实现字符串每个字符双重出现，如输入”abc”，输出”aabbcc”

solution:
(1)

```
const doubleChar = (str) => str.split("").map(c => c + c).join("");
```

(2)

```
function doubleChar(str) {
  return str.replace(/(.)/g, "$1$1");
}
```

说明：
1) const为常量，也是ES6中新增的关键字。
2) map为数组迭代方法，返回原始数组每一项经过函数变换后新的值组成的新数组。
3) 正则表达式中 . 表示除换行符\n以外的任何字符；$1表示匹配到的第一个子字符串（还有$2,$3…指的是正则中第几个()里的子字符串部分，如果有匹配到的话）