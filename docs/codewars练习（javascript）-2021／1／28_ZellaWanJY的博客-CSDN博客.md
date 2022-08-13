<!--yml
category: codewars
date: 2022-08-13 11:49:51
-->

# codewars练习（javascript）-2021/1/28_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113317650?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-113317650.nonecase](https://blog.csdn.net/FemaleHacker/article/details/113317650?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-113317650.nonecase)

## codewars-js练习

### 2021/1/28

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Simple Fun #176: Reverse Letter】

Given a string `str`, reverse it omitting all non-alphabetic characters.

**<mark>example</mark>**：

```
For str = "krishan", the output should be "nahsirk".

For str = "ultr53o?n", the output should be "nortlu". 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function reverseLetter(str) {
 			console.log(str);

 			var strArr = str.match(/[a-zA-Z]/g);

 			var arr = [];

 			for(var i=0;i<strArr.length;i++){
 				arr.unshift(strArr[i]);
 			}

 			result = arr.join('');
 			return result;
 		}

		console.log(reverseLetter("krishan"));
		console.log(reverseLetter('ultr53o?n')); </script> 
```

#### 【2】<7kyu>【Find the middle element】

As a part of this Kata, you need to create a function that when provided with a triplet, returns the index of the numerical element that lies between the other two elements.

The input to the function will be an array of three distinct numbers (Haskell: a tuple).

**您需要创建一个函数，当提供三元组时，返回位于其他两个元素之间的数值元素的索引。函数的输入将是一个由三个不同数字组成的数组(Haskell:一个元组)。**

**<mark>example</mark>**：

```
gimme([2, 3, 1]) 
gimme([5, 10, 14]) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> var gimme = function (inputArray) {

			var arr = JSON.parse(JSON.stringify(inputArray))

 			inputArray.sort((a,b) =>{return b-a;});

			for(var i=0;i<arr.length;i++){
				if(arr[i] == inputArray[1]){
					return i;
				}
			}
 		};

		console.log(gimme([2, 3, 1]));
		console.log(gimme([5,10,14])); </script> 
```

#### 【3】<7kyu>【Vowel Count】

Return the number (count) of vowels in the given string.

We will consider `a, e, i, o, u` as vowels for this Kata (but not `y`).

The input string will only consist of lower case letters and/or spaces.

**返回给定字符串中元音的数量(count)。输入只包含小写字母或空格**

**<mark>example</mark>**：

```
getCount("abracadabra") 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function getCount(str) {
 			console.log(str)
  			var vowelsCount = 0;

  			var result = str.match(/[aeiou]/g);
  			console.log(result);
  			if(result == null){
  				return 0;
  			}
  			vowelsCount = result.length;
  			return vowelsCount;
  		}

		console.log(getCount("abracadabra"));
		console.log(getCount('my pyx')) </script> 
```

#### 【4】<7kyu>【Alternate capitalization】

Given a string, capitalize the letters that occupy even indexes and odd indexes separately, and return as shown below. Index `0` will be considered even.

**给定一个字符串，将占用偶数索引和奇数索引的字母分别大写，并返回如下所示。索引0将被认为是偶数。**

**<mark>example</mark>**：

```
capitalize("abcdef") 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function capitalize(s){
 			var arr = s.split('');

 			var arr2 = JSON.parse(JSON.stringify(arr))
 			var len = arr.length;
 			var result =[];
 			for(var i=0;i<len;i++){

 				if(i % 2 == 0){

 					arr.splice(i,1,arr[i].toUpperCase());
 				}else{

 					arr2.splice(i,1,arr[i].toUpperCase());
 				}
 			}
 			result.push(arr.join(''));
 			result.push(arr2.join(''));
 			return result;
 		}

		console.log(capitalize("abcdef"));
		console.log(capitalize("codewarriors")); </script> 
```

#### 【5】<7kyu>【Form The Minimum】

Given a list of digits, return the smallest number that could be formed from these digits, using the digits only once (ignore duplicates).

**给定一个数字列表，返回可以由这些数字组成的最小数字，只使用这些数字一次(忽略重复)。**

**<mark>example</mark>**：

```
minValue ([1, 3, 1])  
minValue([5, 7, 5, 9, 7]) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function minValue(values){
 			var temp = [];
 			for(var i=0;i<values.length;i++){
 				if(temp.indexOf(values[i])== -1){
 					temp.push(values[i]);
 				}
 			}

 			var len = temp.length;

 			temp.sort((a,b)=>{return a-b;});

 			var result = parseInt(temp.join(''));
 			return result;
 		}

		console.log(minValue([1,3,1]));
		console.log(minValue([5,7,5,9,7])); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>