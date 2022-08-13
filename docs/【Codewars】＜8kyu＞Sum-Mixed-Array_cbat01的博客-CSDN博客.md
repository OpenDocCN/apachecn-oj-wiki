<!--yml
category: codewars
date: 2022-08-13 11:52:11
-->

# 【Codewars】＜8kyu＞Sum Mixed Array_cbat01的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_36270908/article/details/112277925?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-112277925.nonecase](https://blog.csdn.net/weixin_36270908/article/details/112277925?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-112277925.nonecase)

## 题目

> **Given an array of integers as strings and numbers, return the sum of the array values as if all were numbers.
> Return your answer as a number.**
> 
> 这道题目要我们实现的是，计算数组所有项的和，数组包含数字跟字符串，如果是字符串的话，转成数字计算。结果返回数字类型。

即使用js计算数组各项总和，数组可能包括字符串

## 例子

```
sumMix([9, 3, '7', '3'])  
sumMix(['5', '0', 9, 3, 2, 1, '9', 6, 7])  
sumMix(['3', 6, 6, 0, '5', 8, 5, '6', 2,'0']) 
```

## 题解一

```
function sumMix(x){
    return x.reduce((sum,a) => sum + +a, 0);  
} 
```

`+a` 表示将字符串转成数字类型

通过`recude()`实现，其中`reduce()`中的参数`0`代表传递给函数的初始值。如果该参数有传，则`sum`默认值为该参数。没传的话，`sum`默认取数组第一项，可能是字符串，所以此处需要传默认值`0`。而题解二先通过`map()`将所有项转换成数字类型，所以不需要这个步骤。

关于reduce()方法的详细介绍可以看我的另一篇播客

## 题解二

```
function sumMix(x){
  return x.map(a => +a).reduce((a, b) => a + b);
} 
```

## 题解三

通过`map()`方法实现：

```
function sumMix(x){
    var sum = 0;
    x.map(n => sum += parseInt(n));
    return sum;
} 
```