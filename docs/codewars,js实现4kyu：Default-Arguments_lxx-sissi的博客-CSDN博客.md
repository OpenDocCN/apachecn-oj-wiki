<!--yml
category: codewars
date: 2022-08-13 11:51:14
-->

# codewars,js实现4kyu:Default Arguments_lxx-sissi的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_35438535/article/details/106874609?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-106874609.nonecase](https://blog.csdn.net/sinat_35438535/article/details/106874609?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-106874609.nonecase)

## 题目简介

[该kata的链接地址](https://www.codewars.com/kata/52605419be184942d400003d/train/javascript)

Write a function defaultArguments. It takes a function as an argument, along with an object containing default values for that function’s arguments, and returns another function which defaults to the right values.

You cannot assume that the function’s arguments have any particular names.

You should be able to call defaultArguments repeatedly to change the defaults.

```
function add(a,b) { return a+b;};
var add_ = defaultArguments(add,{b:9});
add_(10); 
add_(10,7); 
add_(); 

add_ = defaultArguments(add_,{b:3, a:2});
add_(10); 
add_(); 

add_ = defaultArguments(add_,{c:3}); 
add_(10); 
add_(10,10); 
```

HINT: This problem requires using `Fuction.prototype.toString()` in order to extract a function’s argument list

## Example

```
function add(a,b) { return a+b; }
var add_ = defaultArguments(add,{b:9});
Test.assertEquals(add_(10), 19);
Test.assertEquals(add_(10,5), 15);

var add_ = defaultArguments(add_,{b:3});
Test.assertEquals(add_(10), 13);

function add(_id) { return _id; }
Test.assertEquals(defaultArguments(add,{_id:'test'})(unbdefined), undefined);

function add(a,
			b ) { return a+b; }
Test.assertEquals(defaultArguments(add,{b:1})(5), 6); 
```

## 最终代码

```
function defaultArguments(func, params) {

  var args = func.toString().replace(/\/\/.*/gm, '')
            .replace(/\/\*.*?\*\//g, '')
            .replace(/\s+/g, '').match(/\(.*?\)/).join('').replace(/[\(\)]/gi,'').split(',');
        function sum(...num){
            num = num.map(x=> {return x==undefined ? 'un' : x} );
            for (i in params) {
              args.indexOf(i)!=-1 && (num[args.indexOf(i)] == undefined) && (num[args.indexOf(i)] = params[i])
            }
            num = num.map(x=>{return x=='un' ? undefined : x})
            sum.toString = function(){
               return func.toString()
            }
              return num.length != args.length ? NaN : func(...num)
        };
    return sum;
} 
```

## 解题思路

## 难点