<!--yml
category: codewars
date: 2022-08-13 11:47:05
-->

# codewars练习（javascript）-2021/1/24_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113092600?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-113092600.nonecase](https://blog.csdn.net/FemaleHacker/article/details/113092600?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-113092600.nonecase)

## codewars-js练习

### 2021/1/24

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Sum The Strings】

Create a function that takes 2 positive integers in form of a string as an input, and outputs the sum (also as a string):

**<mark>example</mark>**：

```
sumStr("4", "5")    
 sumStr("34", "5") 
```

<mark>**solution：**</mark>

```
<script type="text/javascript"> function sumStr(a,b) {
 			var sum = +a + +b;
 			console.log(sum);
 			return sum.toString();
 		}

		console.log(sumStr("4", "5") ); </script> 
```

#### 【2】<6kyu>【Write Number in Expanded Form】

You will be given a number and you will need to return it as a string in [Expanded Form](https://www.mathplacementreview.com/arithmetic/whole-numbers.php#expanded-form).

**<mark>example</mark>**：

```
expandedForm(12); 
expandedForm(42); 
expandedForm(70304); 
```

<mark>**思路：**</mark>

*   先将num切割放入到数组中；
*   遍历数组并进行运算，然后将非0的数字放入到新的数组中；
*   最后将新数组中的数据通过+进行连接

<mark>**solution：**</mark>

```
<script type="text/javascript"> function expandedForm(num) {

 			var arr = num.toString().split('');

 			var length = arr.length;
 			var newArr = [];
 			for(var i=0;i<length;i++){
 				var str = arr[i] * Math.pow(10,length-i-1);

 				if(str !=0){
 					newArr.push(str);
 				}
 			}

 			return newArr.join(' + ');
 		}

		console.log(expandedForm(12)); 
		console.log(expandedForm(42)); 
		console.log(expandedForm(70304)); </script> 
```

#### 【3】<7kyu>【String ends with?】

Complete the solution so that it returns true if the first argument(string) passed in ends with the 2nd argument (also a string).

**<mark>example</mark>**：

```
solution('abc', 'bc') 
solution('abc', 'd') 
```

<mark>**solution：**</mark>

```
<script type="text/javascript"> function solution(str, ending){

 			var temp = str.endsWith(ending);
 			return temp;
 		}

		console.log(solution('abc', 'bc')); 
		console.log(solution('abc', 'd')); 
		console.log(solution('abcde', 'abc')) </script> 
```

**<mark>知识点</mark>**

*   **startsWith(anotherString)**
*   **endsWith(anotherString)**

```
"abcd".startsWith("ab"); 
"abcd".startsWith("bc"); 
"abcd".endsWith("cd");   
"abcd".endsWith("e");    
"a".startsWith("a");     
"a".endsWith("a"); 
```

#### *【4】*<6kyu>【Delete occurrences of an element if it occurs more than n times】

Given a list lst and a number N, create a new list that contains each number of lst at most N times without reordering. For example if N = 2, and the input is [1,2,3,1,2,1,2,3], you take [1,2,3,1,2], drop the next [1,2] since this would lead to 1 and 2 being in the result 3 times, and then take 3, which leads to [1,2,3,1,2,3].

**<mark>example</mark>**：

```
deleteNth ([1,1,1,1],2) 

deleteNth ([20,37,20,21],1) 
```

<mark>**solution：**</mark>

```
<script type="text/javascript"> function deleteNth(arr,n){

 			if(!arr){return null;}

 			if(n < 1){return [];}

 			var result = [];
 			var itemCounts = {};

 			for(var i=0;i<arr.length;i++){
 				var item = arr[i];
 				var count = itemCounts[item] ||0;

 				if(count < n){
 					result.push(item);
 					itemCounts[item] = count+1;
 				}
 			}

 			return result;

 		}				

		console.log(deleteNth ([1,1,1,1],2)); 
		console.log(deleteNth ([20,37,20,21],1)); </script> 
```

#### *【5】*<6kyu>【Vasya - Clerk】

The new “Avengers” movie has just been released! There are a lot of people at the cinema box office standing in a huge line. Each of them has a single `100`, `50` or `25` dollar bill. An “Avengers” ticket costs `25 dollars`.

Vasya is currently working as a clerk. He wants to sell a ticket to every single person in this line.

Can Vasya sell a ticket to every person and give change if he initially has no money and sells the tickets strictly in the order people queue?

Return `YES`, if Vasya can sell a ticket to every person and give change with the bills he has at hand at that moment. Otherwise return `NO`.

**<mark>example</mark>**：

```
tickets([25, 25, 50]) 
tickets([25, 100]) 
tickets([25, 25, 50, 50, 100]) 
```

**<mark>思路</mark>**

*   **如果是25，就收下，所以n25++;；**
*   **如果是50，也收下，但要找25，所以n50+; n25–;；**
*   **如果是100，收下，先找25，再判断n50是否大于0，如果还有50则优先找50，没有就找2张25，所以n25–; n50>0?n50–:n25-=2;；**

<mark>**solution：**</mark>

```
<script type="text/javascript"> function tickets(peopleInLine){

 			var len = peopleInLine.length;
 			var [n25,n50,n100] = [0,0,0];
 			for(let v of peopleInLine){
 				if(v == 25) n25++;
 				if(v == 50) {n50++; n25--;}
 				if(v == 100){n25--; n50>0?n50--:n25-=2;}
 				if(n25<0 || n50<0) return 'NO';

 			}
 			return 'YES';			
 		}

		console.log(tickets([25, 25, 50, 50])); 
		console.log(tickets([25, 100])); 
		console.log(tickets([25, 25, 50, 50, 100])); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>