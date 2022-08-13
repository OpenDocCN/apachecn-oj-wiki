<!--yml
category: codewars
date: 2022-08-13 11:40:07
-->

# codewars练习（javascript）-2021/2/8_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113751671?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-113751671.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/113751671?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-113751671.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/2/8

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Evens and Odds】

This kata is about converting numbers to their binary or hexadecimal representation:

*   If a number is even, convert it to binary.
*   If a number is odd, convert it to hex.

将数字转换成二进制或十六进制表示的:

如果一个数是偶数，就把它转换成二进制数。如果一个数字是奇数，将其转换为十六进制。

**<mark>example</mark>**：

```
(2));
(13)); 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function evensAndOdds(num){

 			if(num % 2 == 0){
 				return num.toString(2);
 			}else{
 				return parseInt(num).toString(16);
 			}
 		}

		console.log(evensAndOdds(2));
		console.log(evensAndOdds(13)); </script> 
```

#### 【2】<7kyu>【Life Path Number】

一个人的生命路径号是通过将其出生日期中的每个数字相加计算出来的，直到它减少为一个数字。

**<mark>example</mark>**：

```
year: 1 + 8 + 7 + 9 = 25; 2 + 5 = 7
month: 0 + 3 = 3
day: 1 + 4 = 5
final result: 7 + 3 + 5 = 15; 1 + 5 = 6 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function lifePathNumber(dateOfBirth) {

 			var arr = dateOfBirth.split('-').join('').split('');

 			var year1 = parseInt(arr[0]) + +arr[1] + +arr[2] + +arr[3];

 			var year = Math.floor(year1 / 10) + year1 % 10;

 			var mouth = parseInt(arr[4]) + +arr[5];
 			var day = parseInt(arr[6]) + +arr[7];

 			var final = year + mouth + day;

 			var lifenum = (Math.floor(final / 10) + final % 10);
 			if(lifenum % 10 == 0){
 				lifenum = (Math.floor(lifenum / 10) + lifenum % 10);
 			}
  			return lifenum;
  		}

		console.log(lifePathNumber("1879-03-14"));
		console.log(lifePathNumber("1815-12-10"));
		console.log(lifePathNumber('1961-07-04')); </script> 
```

#### 【3】<7kyu>【Flatten and sort an array】

Given a two-dimensional array of integers, return the flattened version of the array with all the integers in the sorted (ascending) order.

给定一个二维整数数组，返回该数组的扁平版本，其中所有整数按排序(升序)顺序排列。

**<mark>example</mark>**：

```
Given [[3, 2, 1], [4, 6, 5], [], [9, 7, 8]], your function should return [1, 2, 3, 4, 5, 6, 7, 8, 9]. 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function flattenAndSort(array) {

			var arr = [];
			if(array.length !=0){
				for(var i=0;i<array.length;i++){
					for(var j=0;j<array[i].length;j++){

						arr.push(array[i][j]);
					}
				}

				arr.sort((a,b)=>{return a-b;});
				for(var z=0;z<arr.length;z++){
					arr[z] = parseInt(arr[z]);
				}

			  	return arr;
			 }else{
			 	return array;
			 }
		}

		console.log(flattenAndSort([[3, 2, 1], [4, 6, 5], [], [9, 7, 8]]));
		console.log(flattenAndSort([[1, 3, 5], [100], [2, 4, 6]])); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>