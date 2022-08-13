<!--yml
category: codewars
date: 2022-08-13 11:44:31
-->

# codewars:js实现5kyu:A Chain adding function_lxx-sissi的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_35438535/article/details/106298065?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-106298065.nonecase](https://blog.csdn.net/sinat_35438535/article/details/106298065?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-106298065.nonecase)

# 题目描述

该kata的链接: [link](https://www.codewars.com/kata/539a0e4d85e3425cb0000a88).
We want to create a function that will add numbers together when called in succession.

```
add(1)(2); 
```

We also want to be able to continue to add numbers to our chain.

```
add(1)(2)(3); 
add(1)(2)(3)(4); 
add(1)(2)(3)(4)(5); 
```

and so on.

A single call should return the number passed in.

```
add(1); 
```

We should be able to store the returned values and reuse them.

```
var addTwo = add(2);
addTwo; 
addTwo + 5; 
addTwo(3); 
addTwo(3)(5); 
```

We can assume any number being passed in will be valid whole number.

# Example

```
Test.expect(add(1) == 1);
Test.expect(add(1)(2) == 3);
Test.expect(add(1)(2)(3) == 6); 
```

# 我完成的代码

```
function add (num) {
    var count = num;
    var sum = function(num2){ 
        count += num2;
        return sum
    }
    sum.valueOf = function(){
        return count  
    }
    return sum
} 
```

# 我的思路

原谅我作为一个合格的菜鸟，一开始我看到这个题目的时候是这样的，![在这里插入图片描述](img/734578c9b4f26734e6e8ad69901d1574.png)
思考了一下是这样的，![在这里插入图片描述](img/8799cd4eaca69b12fff14d85407387d5.png)
这是个啥？？？为啥我题目都不太懂？？？天啦我怎么这么菜！
但是俗话说得好，不想飞的菜鸟不是好菜鸟，于是我打开了百度…
原来这是**链式函数（一个函数可以无限次调用，需要 return 同一个 function）**，链式函数我会研究一下然后另外做个笔记。

题目的意思是将每一次的传参求和，add()函数要返回一个函数sum()，并且sum()内部也需要返回它本身，这样才能完成连续传参求和的操作。
那么问题来了，我函数返回的是函数，我怎么得出最后的和呢，当然作为一个合格的菜鸟，这个问题我也不会，于是我又打开了百度…
![在这里插入图片描述](img/734578c9b4f26734e6e8ad69901d1574.png)
原来可以重写函数的toString()方法和valueOf()方法来实现，
修改其toString和valueof方法，目的是为了在进行类型转化时返回值。
它可以在返回函数的同时返回它的值

```
sum.valueOf = function(){
        return count  
    } 
```

# 我的难点

知识点的不足！！！
勤能补拙！！！