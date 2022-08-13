<!--yml
category: codewars
date: 2022-08-13 11:46:43
-->

# codewars练习（javascript）-2021/1/23_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113062518?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-113062518.nonecase](https://blog.csdn.net/FemaleHacker/article/details/113062518?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-113062518.nonecase)

## codewars-js练习

### 2021/1/23

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Find the position!】

When provided with a letter, return its position in the alphabet.

Input :: “a”

Ouput :: “Position of alphabet: 1”

**<mark>example</mark>**：

```
position("a"),"Position of alphabet: 1"); 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> function position(letter){
 			console.log(letter)
 			var result =  letter.charCodeAt()-96;
 			return "Position of alphabet: " + result;
		}

		console.log(position("a")); </script> 
```

#### 【2】<6kyu>【Count characters in your string】

The main idea is to count all the occurring characters in a string. If you have a string like `aba`, then the result should be `{'a': 2, 'b': 1}`.

What if the string is empty? Then the result should be empty object literal, `{}`.

**<mark>example</mark>**：

```
count("aba")
count("") 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> function count (string) {  

 			var count = {};

		    var arr = string.split('');

		    arr.forEach(function(s){
		        count[s] ? count[s]++ : count[s] = 1;
		    })
		    return count;
		}

		console.log(count("aba"));
		console.log(count('')); </script> 
```

#### 【3】<7kyu>【Testing 1-2-3】

Write a function which takes a list of strings and returns each line prepended by the correct number.

The numbering starts at 1\. The format is `n: string`. Notice the colon and space in between.

**<mark>example</mark>**：

```
number([]) 
number(["a", "b", "c"]) 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> var number=function(array){
 			var len = array.length;
 			if(len ==0){
 				return [];
 			}else{
 				for(var i=0;i<len;i++){

 					array.splice(i,1,parseInt(i+1)+ ": "+ array[i]);
 				}
 				return array;
 			}
 		}

		console.log(number([])); 
		console.log(number(["a", "b", "c"])); </script> 
```

#### 【4】<8kyu>【Sum of differences in array】

Your task is to sum the differences between consecutive pairs in the array in descending order.

**<mark>example</mark>**：

```
For example:

sumOfDifferences([2, 1, 10])
Returns 9

Descending order: [10, 2, 1]

Sum: (10 - 2) + (2 - 1) = 8 + 1 = 9 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> function sumOfDifferences(arr) {

 			arr = arr.sort(function(a,b){return b-a;});
 			var arr1 = [];
 			var result = 0;
 			for(var i=0;i<arr.length-1;i++){
 				var sum = arr[i] - arr[i+1];
 				arr1.push(sum);
 			}
 			for(var j=0;j<arr1.length;j++){
 				var result = result + arr1[j];
 			}
 			return result;
 		}

		console.log(sumOfDifferences([-3, -2, -1])); 
		console.log(sumOfDifferences([1, 2, 10])); </script> 
```

#### *【5】*<6kyu>【Sort the odd】

You will be given an array of numbers. You have to sort the odd numbers in ascending order while leaving the even numbers at their original positions.

<mark>即 你必须把奇数按升序排序，而把偶数保留在原来的位置。</mark>

**<mark>example</mark>**：

```
[7, 1]  =>  [1, 7]
[5, 8, 6, 3, 4]  =>  [3, 8, 6, 5, 4]
[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]  =>  [1, 8, 3, 6, 5, 4, 7, 2, 9, 0] 
```

<mark>**思路：**</mark>

*   先将奇数和对应的index放在新数组
*   对奇数升序排序
*   将原数组中奇数部分替换成新的

<mark>**solution：**</mark>

```
<script type="text/javascript"> function sortArray(array) {

 			var oddArr = [];

 			var oddIndex = [];

 			for(var i=0;i<array.length;i++){
 				if(array[i]%2!=0){
 					oddArr.push(array[i]);
 					oddIndex.push(i);
 				}
 			}

 			oddArr.sort((a,b)=>{return a-b;});

 			for(var j=0;j<oddArr.length;j++){

 				array[oddIndex[j]] = oddArr[j];
 			}

 			return array;
 		}

		console.log(sortArray([5, 3, 2, 8, 1, 4])); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>