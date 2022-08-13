<!--yml
category: codewars
date: 2022-08-13 11:37:44
-->

# codewars练习（javascript）-2021/2/5_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113702301?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-113702301.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/113702301?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-113702301.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/2/5

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<5kyu>【Regex Password Validation】

You need to write regex that will validate a password to make sure it meets the following criteria:

*   At least six characters long
*   contains a lowercase letter
*   contains an uppercase letter
*   contains a number

Valid passwords will only be alphanumeric characters.

您需要编写正则表达式来验证密码，以确保它符合以下条件:

至少6个字符/包含小写字母/包含大写字母/包含许多/有效的密码只能是字母数字字符。

**<mark>example</mark>**：

```
('djI38D55'), 'djI38D55 - Expected true'
('a2.d412'), 'a2.d412 - Expected false' 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function validate(password) {
 	 		return /^(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])\w{6,}$/g.test(password);
		}

		console.log(validate('djI38D55')); 
		console.log(validate('a2.d412')); 
		console.log(validate('123'));
		console.log(validate('jfkdfj3j'));
		console.log(validate('JHD5FJ53')); </script> 
```

#### 【2】<6kyu>【Two Sum】

Write a function that takes an array of numbers (integers for the tests) and a target number. It should find two different items in the array that, when added together, give the target value. The indices of these items should then be returned in a tuple like so: `(index1, index2)`.

**返回相加等于目标和的两个index**

**<mark>example</mark>**：

```
twoSum [1, 2, 3] 4 
twoSum [1234,5678,9012] 14690 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function twoSum(numbers, target) {

 			for(var i=0;i<numbers.length;i++){
 				for(var j=i+1;j<numbers.length;j++){
 					if(numbers[i] + numbers[j] == target){

 						return [i,j];
 					}
 				}			
 			}
 		}

		console.log(twoSum([1,2,3],4)); 
		console.log(twoSum([1234,5678,9012],14690)); </script> 
```

#### 【3】<5kyu>【String incrementer】

Your job is to write a function which increments a string, to create a new string.

*   If the string already ends with a number, the number should be incremented by 1.
*   If the string does not end with a number. the number 1 should be appended to the new string.

**你的工作是写一个函数来增加一个字符串，来创建一个新的字符串。**

**如果字符串已经以一个数字结束，则该数字应该加1;如果字符串没有以数字结束。数字1应该被附加到新的字符串中。**

**<mark>example</mark>**：

```
foo -> foo1

foobar23 -> foobar24

foo0042 -> foo0043

foo9 -> foo10

foo099 -> foo100 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function incrementString (strng) {
 			console.log(strng);
 			var arr = strng.split('');
 			var num = strng.match(/(\d*)$/)[0];

 			var len = strng.length - num.length;
 			if(num !=0){
 				for(var i=num.length-1;i>0;i--){
 					if(parseInt(num[i])==0){

 						if(strng.substring(strng.length-1,strng.length) == 9){
 							return strng.substring(0,len+i) + (parseInt(num)+1);
 						}
 						return strng.substring(0,len+i+1) + (parseInt(num)+1);

 					}
 				}
 				return strng.substring(0,len) + (parseInt(num)+1);
 			}else{
 				console.log((/0{1,}/g).test(num))

 				if((/0{1,}/g).test(num)){
 					for(var i=num.length-1;i>0;i--){
 					if(parseInt(num[i])==0){
 						return strng.substring(0,len+i) + (parseInt(num)+1);
 					}
 				}
 				}else{
 					return strng + '1';
 				}

 			}

 		}

		console.log(incrementString('foo')); 

		console.log(incrementString('foobar000')) </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。最后一道祈求最优解，感觉我写的很繁琐</mark>