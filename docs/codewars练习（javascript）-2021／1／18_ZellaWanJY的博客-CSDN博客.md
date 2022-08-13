<!--yml
category: codewars
date: 2022-08-13 11:46:45
-->

# codewars练习（javascript）-2021/1/18_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/112771467?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-112771467.nonecase](https://blog.csdn.net/FemaleHacker/article/details/112771467?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-112771467.nonecase)

## codewars-js练习

### 2021/1/18

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.<mark>（即删除数组中的字符串）</mark>

**<mark>example</mark>**：

```
filter_list([1,2,'a','b']) == [1,2]
filter_list([1,'a','b',0,15]) == [1,0,15]
filter_list([1,2,'aasf','1','123',123]) == [1,2,123] 
```

**<mark>思路：</mark>**

*   创建新数组，用来放置原数组除去string类型的其他元素
*   判断原数组中不是string类型的元素
*   将其放入到新数组中

**<mark>solution：</mark>**

```
<script type="text/javascript">
 		function filter_list(l) {

 			var newL = [];
 			for(var i=0;i<l.length;i++){

 				if(typeof l[i]!='string'){
 					newL.push(l[i]);
 				}
 			}

 			return newL;
		}

		var test1 = filter_list([1,2,'a','b']);
		var test2 = filter_list([1,'a','b',0,15]);
		var test3 = filter_list([1,2,'aasf','1','123',123]);
		console.log(test1);
		console.log(test2);
		console.log(test3);
	</script> 
```

#### 【2】Complete the method that takes a boolean value and return a `"Yes"` string for `true`, or a `"No"` string for `false`.<mark>（即遇到true返回Yes，遇到fasle返回No）</mark>

**<mark>example</mark>**：

```
boolToWord(true), 'Yes'
boolToWord(false), 'No' 
```

**<mark>solution：</mark>**

```
<script type="text/javascript">
 		function boolToWord( bool ){
		  if(bool == true){
		  	return 'Yes';
		  }else{
		  	return 'No';
		  }
		}

		console.log(boolToWord(false));
	</script> 
```

#### 【3】Create a function that returns the sum of the two lowest positive numbers given an array of minimum 4 positive integers. No floats or non-positive integers will be passed.<mark>（即返回数组中最小两个正整数的和）</mark>

**<mark>example</mark>**：

```
[19, 5, 42, 2, 77]
[10, 343445353, 3453445, 3453545353453] 
```

**<mark>思路：</mark>**

**<mark>solution：</mark>**

```
<script type="text/javascript">
 		function sumTwoSmallestNumbers(numbers) {

 			numbers = numbers.sort(function (x,y) {
      								return x-y;
    								});

 			var sum = numbers[0]+numbers[1];
 			return sum;
		}

		console.log(sumTwoSmallestNumbers([5, 8, 12, 19, 22]));
		console.log(sumTwoSmallestNumbers([15, 28, 4, 2, 43]));
	</script> 
```

#### 【4】Simple, given a string of words, return the length of the shortest word(s).<mark>（即返回最短单词的长度）</mark>

**<mark>example</mark>**：

```
findShort("bitcoin take over the world maybe who knows perhaps")
findShort("turns out random test cases are easier than writing out basic ones") 
```

**<mark>思路：</mark>**

*   先将字符串按空格分割；
*   遍历获取每个单词的长度，并放入数组中
*   对数组进行升序排序，返回最小长度

**<mark>solution：</mark>**

```
<script type="text/javascript">
 		function findShort(s){

 			var arr  = s.split(' ');

 			var lengthArr = [];

 			var minLength = 0;

 			for(var i=0;i<arr.length;i++){
 				lengthArr.push(arr[i].length);
 			}

 			lengthArr = lengthArr.sort(function(x,y){
 				return x-y;
 			});

 			minLength = lengthArr[0];
 			return minLength;
		}

		console.log(findShort("bitcoin take over the world maybe who knows perhaps"));
		console.log(findShort("turns out random test cases are easier than writing out basic ones"));
	</script> 
```

#### 【5】Implement the function unique_in_order which takes as argument a sequence and returns a list of items without any elements with the same value next to each other and preserving the original order of elements.<mark>（即删除相邻的重复元素）</mark>

**<mark>example</mark>**：

```
uniqueInOrder('AAAABBBCCDAABBB') == ['A', 'B', 'C', 'D', 'A', 'B']
uniqueInOrder('ABBCcAD')         == ['A', 'B', 'C', 'c', 'A', 'D']
uniqueInOrder([1,2,2,3,3])       == [1,2,3] 
```

**<mark>思路：</mark>**

*   先判断是string类型还是数组，若为string类型则将其分割为数组进行操作；
*   创建临时变量和结果返回数组；
*   遍历原数组，并判断是否相邻又重复；
*   若当前元素与临时变量不等，则加入到返回数组中，并更新临时变量；
*   返回最终返回数组。

**<mark>solution：</mark>**

```
<script type="text/javascript">
 		var uniqueInOrder=function(iterable){

 			if(typeof iterable == 'string'){
 				var arr  = iterable.split('');
 			}else{
 				var arr = iterable;
 			}

		  	var pre_item = 0;

		  	var resultArr = [];

		  	for(var i=0;i<arr.length;i++){
		  			if(arr[i] != pre_item){
		  				resultArr.push(arr[i]);
		  				pre_item = arr[i]; 
		  		}
		  	}
		  	return resultArr;
		}

		uniqueInOrder('ABBCcAD');
		uniqueInOrder('AAAABBBCCDAABBB');
		uniqueInOrder([1,2,2,3,3]) 
		uniqueInOrder([]);
	</script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>