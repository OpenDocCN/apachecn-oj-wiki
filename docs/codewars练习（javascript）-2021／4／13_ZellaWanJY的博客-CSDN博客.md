<!--yml
category: codewars
date: 2022-08-13 11:39:00
-->

# codewars练习（javascript）-2021/4/13_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/115653867?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-13-115653867-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/115653867?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-13-115653867-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/4/13

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### *【1】<5kyu>【Calculating with Functions】*

除法应为整数除法。例如，它应该返回2，而不是2.666666…:

**<mark>example</mark>**：

```
seven(times(five())); 
four(plus(nine())); 
eight(minus(three())); 
six(dividedBy(two())); 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function zero(func)  { return func ? func(0) : 0; };
	function one(func)   { return func ? func(1) : 1; };
	function two(func)   { return func ? func(2) : 2; };
	function three(func) { return func ? func(3) : 3; };
	function four(func)  { return func ? func(4) : 4; };
	function five(func)  { return func ? func(5) : 5; };
	function six(func)   { return func ? func(6) : 6; };
	function seven(func) { return func ? func(7) : 7; };
	function eight(func) { return func ? func(8) : 8; };
	function nine(func)  { return func ? func(9) : 9; };

	function plus(b) {return function(a){return a+b;};}
	function minus(b) {return function(a){return a-b;};}
	function times(b) {return function(a){return a*b;};}
	function dividedBy(b) {return function(a){return a/b;};}

	console.log(seven(times(five())));
	console.log(four(plus(nine())));
	console.log(eight(minus(three())));
	console.log(six(dividedBy(two()))); </script> 
```

#### 【2】<7kyu>【All Star Code Challenge #22】

**<mark>example</mark>**：

```
3600 --> "1 hour(s) and 0 minute(s)"
3601 --> "1 hour(s) and 0 minute(s)"
3500 --> "0 hour(s) and 58 minute(s)"
23500 --> "89 hour(s) and 51 minute(s)" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function toTime(seconds) {
		console.log(seconds)
		var hours = Math.floor(seconds/ 60/ 60);
		if (hours == 0) var minute = Math.floor(seconds/ 60)
		else minute = Math.floor((seconds- hours*60*60) / 60)
		return hours + ' hour(s) and '+ minute + ' minute(s)'
	} </script> 
```

#### 【3】<7kyu>【All Star Code Challenge #24】

hypotenuse()，它接受2个整数参数，即直角三角形的两条正边的长度，并返回缺失的边的长度，即斜边，作为一个数字。

leg()，它接受2个整数参数，第一个是斜边的长度，第二个是直角三角形正边的长度。这个函数应该以数字的形式返回缺失的规则边的长度.

<mark>**solution**</mark>

```
<script type="text/javascript"> function hypotenuse(a, b){
		return Math.sqrt(Math.pow(a,2) + Math.pow(b,2))
	}

	function leg(c, a){
		return Math.sqrt(Math.pow(c,2) - Math.pow(a,2))
	} </script> 
```

#### 【4】<7kyu>【All Star Code Challenge #20】

它将两个长度相等的数组组合在一起，将第一个数组中的每个元素与第二个数组中的相应元素相加，返回“组合”的加和数组。如果输入参数的长度不相等将引发错误。

**<mark>example</mark>**：

```
addArrays([1,2],[4,5]); 
addArrays([1,2,3],[4,5]); 
addArrays(["a"],["b"]) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function addArrays(array1, array2) {
		console.log(array1,array2)
		if(array1.length != array2.length) throw new Error();
		var result = [];
		for(var i=0;i<array1.length;i++){
			result.push(array1[i] + array2[i])
		}
		return result
	} </script> 
```