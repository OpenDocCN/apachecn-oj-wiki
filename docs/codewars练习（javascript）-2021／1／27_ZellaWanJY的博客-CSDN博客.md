<!--yml
category: codewars
date: 2022-08-13 11:50:17
-->

# codewars练习（javascript）-2021/1/27_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/femalehacker/article/details/113244652?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-113244652.nonecase](https://blog.csdn.net/femalehacker/article/details/113244652?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-113244652.nonecase)

## codewars-js练习

### 2021/1/27

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Exes and Ohs】

Check to see if a string has the same amount of 'x’s and 'o’s. The method must return a boolean and be case insensitive. The string can contain any char.

**检查一个字符串是否有相同数量的’x’和’o’。该方法必须返回一个布尔值，且不区分大小写。字符串可以包含任何字符。**

**<mark>example</mark>**：

```
XO("ooxx") => true
XO("xooxx") => false
XO("ooxXm") => true
XO("zpzpzpp") => true 
XO("zzoo") => false 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function XO(str) {

 			var strArr = str.toLowerCase().split('');
 			var xArr = [];
 			var oArr = [];

 			for(var i=0;i<strArr.length;i++){
 				if(strArr[i] == 'x'){
 					xArr.push(strArr[i]);
 				}else if(strArr[i] == 'o'){
 					oArr.push(strArr[i]);
 				}
 			}

 			if(xArr.length == oArr.length){
 				return true;
 			}
 			return false;
 		}

		console.log(XO('xo'));
		console.log(XO("xxOo"));
		console.log(XO("xxxm"));
		console.log(XO("ooom")); </script> 
```

#### 【2】<7kyu>【Find the stray number】

You are given an *odd-length* array of integers, in which all of them are the same, except for one single number.

Complete the method which accepts such an array, and returns that single different number.

**The input array will always be valid!** (odd-length >= 3)

**给定一个奇数长度的整数数组，其中除了一个数字之外，其他都是相同的。完成接受这样一个数组的方法，并返回一个不同的数字。输入数组将始终有效!(奇数长的> = 3)**

**<mark>example</mark>**：

```
[1, 1, 2] 
[17, 17, 3, 17, 17, 17, 17] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function stray(numbers) {
 			console.log(numbers);
 			var len = numbers.length;
 			var map = {};
 			if(len % 2 !=0){
	 			for(var i=0;i<len;i++){

	 				var key = numbers[i];

	 				if(map[key]){
	 					map[key] ++;
	 				}else{
	 					map[key] =1;
	 				}
	 			}

	 			for(var key in map){

	 				if(map[key] == 1){
	 					return parseInt(key);
	 				}
	 			}
 			}
 			return 0;
 		}

		console.log(stray([1,2]));
		console.log(stray([1,1,2]));
		console.log(stray([17,17,3,17,17,17,17]));
		console.log(stray([1,2,1]));
		console.log(stray([8, 1, 1, 1, 1, 1, 1 ])); </script> 
```

#### 【3】<7kyu>【Odd or Even?】

Given a list of numbers, determine whether the sum of its elements is odd or even.

Give your answer as a string matching `"odd"` or `"even"`.

If the input array is empty consider it as: `[0]` (array with a zero).

**<mark>example</mark>**：

```
odd_or_even([0])          ==  "even"
odd_or_even([0, 1, 4])    ==  "odd"
odd_or_even([0, -1, -5])  ==  "even" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function oddOrEven(array) {

 			var sum =0;
 			for(var i=0;i<array.length;i++){
 				sum += array[i];
 			}

 			if(sum %2 == 0){
 				return 'even';
 			}
 			return 'odd';
 		}

		console.log(oddOrEven([0]));
    	console.log(oddOrEven([]));
    	console.log(oddOrEven([0,1,4]));
    	console.log(oddOrEven([-1023, -1, 3])); </script> 
```

#### 【4】<7kyu>【Disemvowel Trolls】

Your task is to write a function that takes a string and return a new string with all vowels removed.

For example, the string “This website is for losers LOL!” would become “Ths wbst s fr lsrs LL!”.

Note: for this kata `y` isn’t considered a vowel.

**编写一个函数，接受一个字符串并返回一个删除了所有元音的新字符串。注意:这个形符y不被认为是元音。**

**<mark>example</mark>**：

```
"This website is for losers LOL!" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function disemvowel(str) {

 			var vowelArr = ['a','A','e','E','i','I','o','O','u','U'];

 			var strArr = str.split('');

 			for(var i=0;i<vowelArr.length;i++){
 				for(var j=0;j<strArr.length;j++){
 					if(vowelArr[i] == strArr[j]){

 						strArr.splice(j,1);
 					}
 				}
 			}
 			var newStr = strArr.join('');

 			return newStr;
 		}

		console.log(disemvowel("This website is for losers LOL!")); </script> 
```

#### *【5】*<6kyu>【Help the bookseller !】

A bookseller has lots of books classified in 26 categories labeled A, B, … Z. Each book has a code `c` of 3, 4, 5 or more characters. The **1st** character of a code is a capital letter which defines the book category.

In the bookseller’s stocklist each code `c` is followed by a space and by a positive integer n (int n >= 0) which indicates the quantity of books of this code in stock.

**获取到此类别的总数量**

**<mark>example</mark>**：

```
b = ["ABAR 200", "CDXE 500", "BKWR 250", "BTSQ 890", "DRTY 600"]
c = ["A", "B"]
res = "(A : 200) - (B : 1140)"
stockList(b, c), res)

b = ["CBART 20", "CDXEF 50", "BKWRK 25", "BTSQZ 89", "DRTYM 60"]
c = ["A", "B", "C", "W"]
res = "(A : 0) - (B : 114) - (C : 70) - (W : 0)"
stockList(b, c), res) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function stockList(listOfArt, listOfCat){
 			if (!listOfArt.length || !listOfCat.length) return ''
 			return listOfCat.map(w => {
    			const s = listOfArt.reduce((a, b) => a + (b.charAt(0) === w ? +b.split(' ')[1] : 0), 0)
    				return `(${w} : ${s})`
  			}).join(' - ')
 		}

		b = ["ABAR 200", "CDXE 500", "BKWR 250", "BTSQ 890", "DRTY 600"]
		c = ["A", "B"]
		console.log(stockList(b, c)); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。(最后一题为大佬思路，绝)</mark>