<!--yml
category: codewars
date: 2022-08-13 11:49:23
-->

# CodeWars —— A Chain adding function_Lee_zz的博客-CSDN博客

> 来源：[https://blog.csdn.net/lee_zz/article/details/116756182?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-116756182.nonecase](https://blog.csdn.net/lee_zz/article/details/116756182?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-116756182.nonecase)

```
add(1); 
add(1)(2); 
add(1)(2)(3); 
add(1)(2)(3)(4); 
add(1)(2)(3)(4)(5); 
```

在我们平时对函数进行 console.log 打印时，会直接将函数的内容打印在控制台上，这是因为隐式地调用了toString方法，将函数转成了字符串输出。

**结果**

```
function add(num){
	let count = num 
	function sum(num2){
		count += num2
		return sum
	}
	sum.toString = () => {
		return count
	}
	return sum
} 
```

在这个方法中：
当 add(1) 时，返回的是sum函数，🈶️因为直接输出一个函数会隐式调用该函数的toString方法，因此
sum.toString（）执行，输出count 为1
当add(1)(2)时，sum函数调用，count被改写为1+2=3，return sum函数，接着调用toString方法，输出当前count
…