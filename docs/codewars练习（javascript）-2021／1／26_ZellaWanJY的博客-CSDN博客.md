<!--yml
category: codewars
date: 2022-08-13 11:46:59
-->

# codewars练习（javascript）-2021/1/26_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113174515?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-113174515.nonecase](https://blog.csdn.net/FemaleHacker/article/details/113174515?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-113174515.nonecase)

## codewars-js练习

### 2021/1/26

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Dollars and Cents】

you have volunteered to create a function that will take a float and return the amount formatting in dollars and cents.

39.99 becomes $39.99

**<mark>example</mark>**：

```
3 needs to become $3.00

3.1 needs to become $3.10 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function formatMoney(amount){
      var count = String(amount).length - (String(amount).indexOf(".") + 				1);
      if(amount % 1 ==0){
          return '$'+amount +'.00';
      }else if(count == 1){
          return '$'+amount +'0';
      }
  return '$'+amount;
 		}

		console.log(formatMoney(39.99)); </script> 
```

#### 【2】<6kyu>【Mexican Wave】

In this simple Kata your task is to create a function that turns a string into a Mexican Wave. You will be passed a string and you must return that string in an array where an uppercase letter is a person standing up.

1.  The input string will always be lower case but maybe empty.

2.  If the character in the string is whitespace then pass over it as if it was an empty seat

**<mark>example</mark>**：

```
wave("hello") => ["Hello", "hEllo", "heLlo", "helLo", "hellO"] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function wave(str){
 			var arr = str.toLowerCase().split('');

 			var result = [];
 			for(var i=0;i<arr.length;i++){
 				var temp = str.substring(0,i) + arr[i].toUpperCase() + str.substring(i+1);
 				if(temp != str){
 					result.push(temp);
 				}
 			}

 			return result;
 		}

		console.log(wave("hello"));
		console.log(wave("gap"));
		console.log(wave("two words")); </script> 
```

#### 【3】<6kyu>【Break camelCase】

Complete the solution so that the function will break up camel casing, using a space between words.

**<mark>example</mark>**：

```
solution("camelCasing")  ==  "camel Casing" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function solution(string) {

			var arr = string.split('');

			var strArr = string.toUpperCase().split('');
			var temp = [];

			for(var i=0;i<arr.length;i++){
				if(arr[i] == strArr[i]){
					temp.push(i);

				}
			}

			var count = 0;
			for(var j=0;j<temp.length;j++){

				arr.splice(temp[j]+count,0,' ');
				count ++;
			}
			return arr.join('');
		}

		console.log(solution("camelCasing"));
		console.log(solution('camelCasingTest')); </script> 
```

#### 【4】<7kyu>【Factorial】

In mathematics, the factorial of a non-negative integer n, denoted by n!, is the product of all positive integers less than or equal to n. For example: 5! = 5 * 4 * 3 * 2 * 1 = 120\. By convention the value of 0! is 1.

Write a function to calculate factorial for a given input. If input is below 0 or above 12 throw a `RangeError` (JavaScript) .

**求阶乘**

**<mark>example</mark>**：

```
factorial(0)
factorial(1)
factorial(2)
factorial(3) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function factorial(n){

 			var i =1;
 			var sum =1;

 				if(n>1 && n<=12){
 					while (i <= n) {
        				sum *= i;
        				i++;
    				}
 					return sum;
 				}else if(n == 0 || n == 1){
 					return 1;
 				}else{throw new RangeError();}
 			}

		console.log(factorial(0));
		console.log(factorial(1));
		console.log(factorial(5));
		console.log(factorial(13)); </script> 
```

#### 【5】<7kyu>【Categorize New Member】

To be a senior, a member must be at least 55 years old and have a handicap greater than 7\. In this croquet club, handicaps range from -2 to +26; the better the player the lower the handicap.

Input will consist of a list of lists containing two items each. Each list contains information for a single potential member. Information consists of an integer for the person’s age and an integer for the person’s handicap.

Note for F#: The input will be of (int list list) which is a List

**[age，handicap]，只有当age>=55 并且handicap>7时才为senior，否则为open**

**<mark>example</mark>**：

```
[[18, 20],[45, 2],[61, 12],[37, 6],[21, 21],[78, 9]] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function openOrSenior(data){
 			var str = '';
 			var result = [];
 			for(var i=0;i<data.length;i++){

 				if(data[i][0]>=55 && data[i][1]>7){
 					str = 'Senior';
 					result.push(str);
 				}else{
 					str = 'Open';
 					result.push(str);
 				}
 			}

 			return result;
 		}

		console.log(openOrSenior([[45, 12],[55,21],[19, -2],[104, 20]]));
		console.log(openOrSenior([[3, 12],[55,1],[91, -2],[54, 23]]));
		console.log(openOrSenior([[59, 12],[55,-1],[12, -2],[12, 12]])); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>