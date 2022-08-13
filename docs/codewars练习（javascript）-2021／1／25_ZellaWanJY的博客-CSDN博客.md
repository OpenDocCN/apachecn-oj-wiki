<!--yml
category: codewars
date: 2022-08-13 11:50:15
-->

# codewars练习（javascript）-2021/1/25_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113111135?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-113111135.nonecase](https://blog.csdn.net/FemaleHacker/article/details/113111135?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-113111135.nonecase)

## codewars-js练习

### 2021/1/25

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Quarter of the year】

Given a month as an integer from 1 to 12, return to which quarter of the year it belongs as an integer number.

For example: month 2 (February), is part of the first quarter; month 6 (June), is part of the second quarter; and month 11 (November), is part of the fourth quarter.

**给定一个月作为从1到12的整数，以整数形式返回它所属的季度。**

**<mark>example</mark>**：

```
quarterOf(3)
quarterOf(8)
 quarterOf(11) 
```

<mark>**solution：**</mark>

```
<script type="text/javascript"> const quarterOf = (month) => {
 			switch(month>0&& month<13){
 				case month>0 && month<=3:

 					return 1;
 					break;
 				case month>3 && month<=6:

 					return 2;
 					break;
 				case month>6 && month<=9:

 					return 3;

 					break;
 				case month>9 && month<=12:

 					return 4;
 					break;
 				default:
 					break;
 			}
 		}

		console.log(quarterOf(3));
		console.log(quarterOf(8)); </script> 
```

#### 【2】<6kyu>【Detect Pangram】

A pangram is a sentence that contains every single letter of the alphabet at least once. For example, the sentence “The quick brown fox jumps over the lazy dog” is a pangram, because it uses the letters A-Z at least once (case is irrelevant).

Given a string, detect whether or not it is a pangram. Return True if it is, False if not. Ignore numbers and punctuation.

**pangram是至少包含一次字母表中每一个字母的句子。即a-z都含有**

**<mark>example</mark>**：

```
var string = "The quick brown fox jumps over the lazy dog."
Test.assertEquals(isPangram(string), true)
var string = "This is not a pangram."
Test.assertEquals(isPangram(string), false) 
```

**思路**

*   先将字符串全部转为大写
*   65-90代表a-z，则循环将65-90转换成a-z；
*   用indexOf进行判断，如果为-1，则说明不存在。

<mark>**solution：**</mark>

```
<script type="text/javascript"> function isPangram(string){

 			var str = string.toUpperCase();

 			for(var i=65;i<90;i++){
 				if(str.indexOf(String.fromCharCode(i)) == -1){
 					return false;
 				}
 			}
 			return true;
 		}

		var string = "The quick brown fox jumps over the lazy dog."
		console.log(isPangram(string));
		var string2 = "This is not a pangram."
		console.log(isPangram(string2)); </script> 
```

#### 【3】<7kyu>【Descending Order】

Your task is to make a function that can take any non-negative integer as an argument and return it with its digits in descending order. Essentially, rearrange the digits to create the highest possible number.

**降序排序**

**<mark>example</mark>**：

```
Input: 42145 Output: 54421

Input: 145263 Output: 654321

Input: 123456789 Output: 987654321 
```

<mark>**solution：**</mark>

```
<script type="text/javascript"> function descendingOrder(n){

 			var arr = n.toString().split('');

 			arr.sort((a,b)=>{return b-a});

 			var result = parseInt(arr.join(''));

 			return result;
 		}

		console.log(descendingOrder(42145));
		console.log(descendingOrder(145263)); </script> 
```

#### 【4】<7kyu>【Highest and Lowest】

In this little assignment you are given a string of space separated numbers, and have to return the highest and lowest number.

**返回最大、最小值**

**<mark>example</mark>**：

```
highAndLow("1 2 3 4 5");  
highAndLow("1 2 -3 4 5"); 
highAndLow("1 9 3 4 -5"); 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function highAndLow(numbers){
 			var numStr = numbers.split(' ');

 			numStr.sort((a,b)=>{return b-a;});

 			return numStr[0] +' '+numStr[numStr.length-1];;
 		}

		console.log(highAndLow("1 2 3 4 5"));
		console.log(highAndLow("1 2 -3 4 5")); </script> 
```

#### 【5】<7kyu>【Sum of all the multiples of 3 or 5】

Upto and including `n`, this function will return the sum of all multiples of 3 and 5.

**查找到n为止所有满足3的倍数或者5的倍数，然后返回这些数的和**

**<mark>example</mark>**：

```
findSum(5) should return 8 (3 + 5)

findSum(10) should return 33 (3 + 5 + 6 + 9 + 10) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function findSum(n) {
 			var sum = 0;

 			for(var i=1;i<=n;i++){
 				if(i % 3==0 || i %5 ==0){

 					sum = sum+i;
 				}
 			}

 			return sum;
 		}

		console.log(findSum(5));
		console.log(findSum(10)); </script> 
```

#### *【6】*<6kyu>【Counting Duplicates】

Write a function that will return the count of **distinct case-insensitive** alphabetic characters and numeric digits that occur more than once in the input string. The input string can be assumed to contain only alphabets (both uppercase and lowercase) and numeric digits.

**Count the number of Duplicates **

**<mark>example</mark>**：

```
"abcde" -> 0 
"aabbcde" -> 2 # 'a' and 'b'
"aabBcde" -> 2 # 'a' occurs twice and 'b' twice (`b` and `B`)
"indivisibility" -> 1 # 'i' occurs six times
"Indivisibilities" -> 2 # 'i' occurs seven times and 's' occurs twice
"aA11" -> 2 # 'a' and '1'
"ABBA" -> 2 # 'A' and 'B' each occur twice 
```

**思路**

*   先将text全部转为小写；然后分隔放到数组中
*   对数组进行sort排序（sort排序是按照unicode编码进行排序）
*   **利用正则表达式，将相同的合并**，然后作为一个整体放在数组中
*   最后读取数组的长度即可

<mark>**solution**</mark>

```
<script type="text/javascript"> function duplicateCount(text){

 			var textArrAfterSort = text.toLowerCase().split('').sort();

 			var newText = textArrAfterSort.join('');

 			var result =  newText.match(/([^])\1+/g);

 			return (result|| []).length;

 		}

		console.log(duplicateCount("abcde"));
		console.log(duplicateCount('aabbcde')); 
		console.log(duplicateCount('indivisibility')); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>