<!--yml
category: codewars
date: 2022-08-13 11:43:01
-->

# codewars解题笔记 —— 匹配字符串_yy406961的博客-CSDN博客

> 来源：[https://blog.csdn.net/yy406961/article/details/78005151?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-78005151.nonecase](https://blog.csdn.net/yy406961/article/details/78005151?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-78005151.nonecase)

题目

What is an anagram? Well, two words are anagrams of each other if they both contain the same letters. For example:

```
'abba' & 'baab' == true

'abba' & 'bbaa' == true

'abba' & 'abbba' == false 
```

Write a function that will find all the anagrams of a word from a list. You will be given two inputs a word and an array with words. You should return an array of all the anagrams or an empty array if there are none. For example:

传入一个字符串和一个数组，将数组中与字符串的字母个数相同的找出来，返回新数组。

我的答案

```
function anagrams(word, words) {
  let str1 = newStr(word)
  let arr = []
  words.forEach(item => {
    let str2 = newStr(item)
    if(str1 === str2){
      arr.push(item)
    }
  })
  return arr
}

function newStr(str){
  let arr = str.split('')
  arr.sort()
  let newStr = arr.join('')
  return newStr
}
```

票数最高的答案

```
String.prototype.sort = function() {
  return this.split("").sort().join("");
};

function anagrams(word, words) {
  return words.filter(function(x) {
      return x.sort() === word.sort();
  });
}
```

思考：

1、首先解题的思路是相同的，给string加API跟自定义一个函数，用到prototype显得高级一些。

2、代码多尝试使用链式解构，看起来会简洁，写代码原则是尽可能的少写

3、filter的使用。面对数组不要总想着forEach。

## filter():  

 语法：

| 

`var`  `filteredArray = array.filter(callback[, thisObject]);`

 |

参数说明：

callback： 要对每个数组元素执行的回调函数。
thisObject ： 在执行回调函数时定义的this对象。

```

```
//过滤掉小于 10 的数组元素：

//代码：
function isBigEnough(element, index, array) {
    return (element >= 10);
}
var filtered = [12, 5, 8, 130, 44].filter(isBigEnough);
// 12, 130, 44
//结果：[12, 5, 8, 130, 44].filter(isBigEnough) ： 12, 130, 44 
```

```

功能说明：

对数组中的每个元素都执行一次指定的函数（callback），并且创建一个新的数组，该数组元素是所有回调函数执行时返回值为 true 的原数组元素。它只对数组中的非空元素执行指定的函数，没有赋值或者已经删除的元素将被忽略，同时，新创建的数组也不会包含这些元素。

回调函数可以有三个参数：当前元素，当前元素的索引和当前的数组对象。

如参数 thisObject 被传递进来，它将被当做回调函数（callback）内部的 this 对象，如果没有传递或者为null，那么将会使用全局对象。

filter 不会改变原有数组，记住：只有在回调函数执行前传入的数组元素才有效，在回调函数开始执行后才添加的元素将被忽略，而在回调函数开始执行到最后一个元素这一期间，数组元素被删除或者被更改的，将以回调函数访问到该元素的时间为准，被删除的元素将被忽略。

filter() 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。

注意： filter() 不会对空数组进行检测。

注意： filter() 不会改变原始数组。