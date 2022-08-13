<!--yml
category: codewars
date: 2022-08-13 11:44:36
-->

# codewars js|Persistent Bugger_千鱼鱼的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41435278/article/details/89332363?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-89332363.nonecase](https://blog.csdn.net/weixin_41435278/article/details/89332363?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-89332363.nonecase)

Write a function, `persistence`, that takes in a positive parameter `num` and returns its multiplicative persistence, which is the number of times you must multiply the digits in `num` until you reach a single digit.

For example

```
 persistence(39) === 3 // because 3*9 = 27, 2*7 = 14, 1*4=4
                       // and 4 has only one digit

 persistence(999) === 4 // because 9*9*9 = 729, 7*2*9 = 126,
                        // 1*2*6 = 12, and finally 1*2 = 2

 persistence(4) === 0 // because 4 is already a one-digit number
```

*   map() 方法通过对原数组中的每个元素进行一定的操作（共同调用一个方法），返回一个新的数组。
    *   用map()方法实现数组的平方：arr.map(x=>{return x*x;})
*   reduce() 方法对累加器和数组的每个值 (从左到右)应用一个函数，以将其减少为单个值。内部实现应该是遍历元素，理论上可以通过forEach方法实现其功能。
    *   用reduce（）实现累加/累乘
        *   var arr=[1,2,3];
        *   var product = function add(x,y){return x+y;}
        *   arr.reduce(product)

我的代码

```
function persistence(num) {
  var arr = num.toString().split('');
  var count = 0;
  var product;

  while (arr.length > 1) {
    product = arr.reduce(function(a, b) {
      return a * b;
    });
    count++;
    arr = product.toString().split("");
  }
  return count;
}
```

计算的是循环次数。。。

大佬的代码：

```
const persistence = num => {
  return `${num}`.length > 1 
    ? 1 + persistence(`${num}`.split('').reduce((a, b) => a * b)) 
    : 0;
}
```