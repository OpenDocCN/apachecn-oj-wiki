<!--yml
category: codewars
date: 2022-08-13 11:49:12
-->

# codewars练习（javascript）-2021/1/19_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/112853791?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-112853791.nonecase](https://blog.csdn.net/FemaleHacker/article/details/112853791?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-112853791.nonecase)

### 文章目录

*   *   [codewars-js练习](#codewarsjs_1)
    *   *   [2021/1/19](#2021119_2)
        *   *   [github 地址](#github__3)
            *   [【1】Write a program that finds the summation of every number from 1 to num. The number will always be a positive integer greater than 0.==（即求1到num的和）==](#1Write_a_program_that_finds_the_summation_of_every_number_from_1_to_num_The_number_will_always_be_a_positive_integer_greater_than_01num_5)
            *   [【2】In this kata, you are asked to square every digit of a number and concatenate them.==（即每位数字分别平方最后连接返回）==](#2In_this_kata_you_are_asked_to_square_every_digit_of_a_number_and_concatenate_them_32)
            *   [*【3】*Implement a function that adds two numbers together and returns their sum in binary. The conversion can be done before, or after the addition.==（即,将两数相加，然后二进制形式返回和）==](#em_stylecolorred3emImplement_a_function_that_adds_two_numbers_together_and_returns_their_sum_in_binary_The_conversion_can_be_done_before_or_after_the_addition_76)
            *   [【4】Very simple, given a number, find its opposite.==（即 取反）==](#4Very_simple_given_a_number_find_its_opposite__180)
            *   [【5】Given an array of ones and zeroes, convert the equivalent binary value to an integer.==（即 将二进制转换成十进制）==](#5Given_an_array_of_ones_and_zeroes_convert_the_equivalent_binary_value_to_an_integer__204)
            *   [【6】Complete the square sum function so that it squares each number passed into it and then sums the results together.==（即 将数组中每位数字求平方相加）==](#6Complete_the_square_sum_function_so_that_it_squares_each_number_passed_into_it_and_then_sums_the_results_together__232)
            *   [*【7】*Given: an array containing hashes of names.Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.](#em_stylecolorred7emGiven_an_array_containing_hashes_of_namesReturn_a_string_formatted_as_a_list_of_names_separated_by_commas_except_for_the_last_two_names_which_should_be_separated_by_an_ampersand_258)
            *   [【8】You are going to be given a word. Your job is to return the middle character of the word. If the word's length is odd, return the middle character. If the word's length is even, return the middle 2 characters.==（如果单词的长度是奇数，则返回中间的字符。如果单词的长度是偶数，则返回中间的2个字符。）==](#8You_are_going_to_be_given_a_word_Your_job_is_to_return_the_middle_character_of_the_word_If_the_words_length_is_odd_return_the_middle_character_If_the_words_length_is_even_return_the_middle_2_characters2_320)
            *   [【9】There is an array with some numbers. All numbers are equal except for one.==（即 找出数组中唯一一个不同的数字）==](#9There_is_an_array_with_some_numbers_All_numbers_are_equal_except_for_one__361)
            *   [【10】 For simplicity, you'll have to capitalize each word, check out how contractions are expected to be in the example below.==（即 将每个单词首字母大写）==](#10_For_simplicity_youll_have_to_capitalize_each_word_check_out_how_contractions_are_expected_to_be_in_the_example_below__390)
            *   [【11】Given two arrays `a` and `b` write a function `comp(a, b)` (`compSame(a, b)` in Clojure) that checks whether the two arrays have the "same" elements, with the same multiplicities. "Same" means, here, that the elements in `b` are the elements in `a` squared, regardless of the order.==（即 检查这两个数组是否具有“相同”的元素和相同的多重性。"相同"的意思是，在这里，b中的元素是a的平方中的元素，无论顺序如何。）==](#11Given_two_arrays_a_and_b_write_a_function_compa_b_compSamea_b_in_Clojure_that_checks_whether_the_two_arrays_have_the_same_elements_with_the_same_multiplicities_Same_means_here_that_the_elements_in_b_are_the_elements_in_a_squared_regardless_of_the_order_ba_426)
            *   [【12】Given an array of integers, remove the smallest value. Do not mutate the original array/list. If there are multiple elements with the same value, remove the one with a lower index. If you get an empty array/list, return an empty array/list.Don't change the order of the elements that are left.**==（即 给定一个整数数组，**删除最小的值**。不要改变原来的数组/列表。如果有**多个具有相同值的元素**，则**删除下标较低**的元素。如果你得到一个空数组/列表，返回一个空数组/列表。不要改变剩下元素的顺序。）==](#12Given_an_array_of_integers_remove_the_smallest_value_Do_not_mutate_the_original_arraylist_If_there_are_multiple_elements_with_the_same_value_remove_the_one_with_a_lower_index_If_you_get_an_empty_arraylist_return_an_empty_arraylistDont_change_the_order_of_the_elements_that_are_left__460)

## codewars-js练习

### 2021/1/19

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】Write a program that finds the summation of every number from 1 to num. The number will always be a positive integer greater than 0.<mark>（即求1到num的和）</mark>

**<mark>example</mark>**：

```
summation(1);
summation(8); 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> var summation = function (num) {
		  var sum = 0;
		  for(var i=0;i<=num;i++){
		  	sum +=i;
		  }
		  return sum;
		}

		console.log(summation(1));
		console.log(summation(8)); </script> 
```

#### 【2】In this kata, you are asked to square every digit of a number and concatenate them.<mark>（即每位数字分别平方最后连接返回）</mark>

**<mark>example</mark>**：

```
For example, if we run 9119 through the function, 811181 will come out, because 92 is 81 and 12 is 1.

squareDigits(9119) 
```

**<mark>思路：</mark>**

*   将number先转换成str，再转换成数组；
*   获取数组每个数字进行平方；
*   将数组转为str，进行连接，最后转换成number进行返回

**<mark>solution：</mark>**

```
<script type="text/javascript"> function squareDigits(num){

 			var str = num.toString();

 			var arr = str.split('');
 			var newArr = [];

 			for(var i=0;i<arr.length;i++){
 				newArr.push(Math.pow(arr[i],2));

 			}

 			var newStr = newArr.join('');

 			var result = Number(newStr);

 			return result;
		}		

		console.log(squareDigits(9119)); </script> 
```

#### *【3】*Implement a function that adds two numbers together and returns their sum in binary. The conversion can be done before, or after the addition.<mark>（即,将两数相加，然后二进制形式返回和）</mark>

**<mark>example</mark>**：

```
addBinary(1,2) 
```

**<mark>思路：</mark>**

**<mark>solution：</mark>**

```
<script type="text/javascript"> function addBinary(a,b) {
 			var sum = a + b;

 			return sum.toString(2);
		}

		console.log(addBinary(1,2));
		console.log(addBinary(0,1)); </script> 
```

**<mark>js进制转换总结：</mark>**

*   **十进制转换成二进制**

    ```
    num.toString(2) 
    ```

*   **二进制转换成十进制**

    ```
    parseInt(num,2) 
    ```

*   八进制转十进制

    ```
    parseInt(num,8) 
    ```

*   十六进制转十进制

    ```
    parseInt(num,16) 
    ```

*   十进制转八进制

    ```
    parseInt(num).toString(8) 
    ```

*   十进制转十六进制

    ```
    parseInt(num).toString(16) 
    ```

*   二进制转八进制

    ```
    parseInt(num,2).toString(8) 
    ```

*   二进制转十六进制

    ```
    parseInt(num,2).toString(16) 
    ```

*   八进制转二进制

    ```
    parseInt(num,8).toString(2) 
    ```

*   八进制转十六进制

    ```
    parseInt(num,8).toString(16) 
    ```

*   十六进制转二进制

    ```
    parseInt(num,16).toString(2) 
    ```

*   十六进制转八进制

    ```
    parseInt(num,16).toString(8) 
    ```

#### 【4】Very simple, given a number, find its opposite.<mark>（即 取反）</mark>

**<mark>example</mark>**：

```
1: -1
14: -14
-34: 34 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> function opposite(number) {
		  return (-number);
		}

		console.log(opposite(1));
		console.log(opposite(14)); </script> 
```

#### 【5】Given an array of ones and zeroes, convert the equivalent binary value to an integer.<mark>（即 将二进制转换成十进制）</mark>

**<mark>example</mark>**：

```
[0,0,0,1]
[1,1,1,1] 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> const binaryArrayToNumber = arr => {

 			var number = arr.join('');

 			var result = parseInt(number,2);
		  	return result;
		};

		console.log(binaryArrayToNumber([0,0,0,1]));
		console.log(binaryArrayToNumber([1,1,1,1])); </script> 
```

#### 【6】Complete the square sum function so that it squares each number passed into it and then sums the results together.<mark>（即 将数组中每位数字求平方相加）</mark>

**<mark>example</mark>**：

```
[1,2,2]
[1,2] 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> function squareSum(numbers){
 			var sum=0;
 			for(var i=0;i<numbers.length;i++){
 				sum += Math.pow(numbers[i],2);
 			}
 			return sum;
		}

		console.log(squareSum([1,2])); </script> 
```

#### *【7】*Given: an array containing hashes of names.Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.

<mark>(除最后两个名称外，其余名称用逗号分隔，它们应该用&号分隔。)</mark>

**<mark>example</mark>**：

```
list([ {name: 'Bart'}, {name: 'Lisa'}, {name: 'Maggie'} ])

list([ {name: 'Bart'}, {name: 'Lisa'} ])

list([ {name: 'Bart'} ])

list([]) 
```

**<mark>思路：</mark>**

*   先获取到名称；
*   获取到输入数组的长度。如果长度为0，直接返回’’；否则获取到name属性放在新数组中
*   然后根据题目要求的分隔符进行分隔。

**<mark>solution：</mark>**

```
<script type="text/javascript"> function list(names){
 			var arr =[];

 			var length = names.length;

 			if(length !=0){
 				for(var i=0;i<names.length-1;i++){
		  			arr.push(names[i].name);
		  		}
 			}else{
 				return '';
 			}

		  	var str = arr.join(', ');
		  	if(str !=''){ 
		  		str = str + ' & ' + names[length-1].name;
		  	}else{
		  		str = names[length-1].name;
		  	}
		  	return str;
		}

		console.log(list([{name: 'Bart'},{name: 'Lisa'},{name: 'Maggie'},{name: 'Homer'},{name: 'Marge'}]));

		console.log(list([{name: 'Bart'},{name: 'Lisa'}]));
		console.log(list([{name: 'Bart'}]));
		console.log(list([])); </script> 
```

#### 【8】You are going to be given a word. Your job is to return the middle character of the word. If the word’s length is odd, return the middle character. If the word’s length is even, return the middle 2 characters.<mark>（如果单词的长度是奇数，则返回中间的字符。如果单词的长度是偶数，则返回中间的2个字符。）</mark>

**<mark>example</mark>**：

```
Kata.getMiddle("test") should return "es"

Kata.getMiddle("testing") should return "t"

Kata.getMiddle("middle") should return "dd"

Kata.getMiddle("A") should return "A" 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> function getMiddle(s){
 			var length = s.length;

 			var index = parseInt(length/2);
 			var arr = [];
 			console.log(index);

 			arr = s.split('');
 			if(length % 2 ==0){
 				 return arr[index-1] + arr[index];
 			}else{
 				return arr[index];
 			}
		}

		console.log(getMiddle("test"));
		console.log(getMiddle("testing"));
		console.log(getMiddle("A")); </script> 
```

#### 【9】There is an array with some numbers. All numbers are equal except for one.<mark>（即 找出数组中唯一一个不同的数字）</mark>

**<mark>example</mark>**：

```
findUniq([ 1, 1, 1, 2, 1, 1 ]) === 2
findUniq([ 0, 0, 0.55, 0, 0 ]) === 0.55 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> function findUniq(arr) {
		  for(var i=0;i<arr.length;i++){
		  	for(var j=i;j<arr.length;j++){
		  		if(arr[i] != arr[j]){
		  			return arr[j];
		  		}
		  	}
		  }
		}

		console.log(findUniq([ 1, 1, 1, 2, 1, 1 ]));
		console.log(findUniq([ 0, 0, 0.55, 0, 0 ])); </script> 
```

#### 【10】 For simplicity, you’ll have to capitalize each word, check out how contractions are expected to be in the example below.<mark>（即 将每个单词首字母大写）</mark>

**<mark>example</mark>**：

```
Not Jaden-Cased: "How can mirrors be real if our eyes aren't real"
Jaden-Cased:     "How Can Mirrors Be Real If Our Eyes Aren't Real" 
```

**<mark>思路：</mark>**

**<mark>solution：</mark>**

```
<script type="text/javascript"> String.prototype.toJadenCase = function () {
		 	var arr = this.toLowerCase().split(" ");
		 	console.log(arr);

			for(var i = 0;i < arr.length;i++){

			    arr[i] = arr[i][0].toUpperCase() + arr[i].substring(1,arr[i].length);
			}

			return arr.join(" ");
		};

		var str = "How can mirrors be real if our eyes aren't real";
		console.log(str.toJadenCase()); </script> 
```

#### 【11】Given two arrays `a` and `b` write a function `comp(a, b)` (`compSame(a, b)` in Clojure) that checks whether the two arrays have the “same” elements, with the same multiplicities. “Same” means, here, that the elements in `b` are the elements in `a` squared, regardless of the order.<mark>（即 检查这两个数组是否具有“相同”的元素和相同的多重性。"相同"的意思是，在这里，b中的元素是a的平方中的元素，无论顺序如何。）</mark>

**<mark>example</mark>**：

```
a = [121, 144, 19, 161, 19, 144, 19, 11] 
b = [11*11, 121*121, 144*144, 19*19, 161*161, 19*19, 144*144, 19*19] 
```

**<mark>思路：</mark>**

*   先将数组中的元素进行平方，放入到新的数组中
*   **newArr.sort().toString() == array2.sort().toString()**用来判断两数组的元素是否全部相同

**<mark>solution：</mark>**

```
<script type="text/javascript"> function comp(array1, array2){
 			var newArr = [];
 			for(var i=0;i<array1.length;i++){
 				newArr.push(Math.pow(array1[i],2));
 			}

 			return (newArr.sort().toString() == array2.sort().toString());
		}

		a1 = [121, 144, 19, 161, 19, 144, 19, 11];
		a2 = [11*11, 121*121, 144*144, 19*19, 161*161, 19*19, 144*144, 19*19];
		console.log(comp(a1,a2)); </script> 
```

#### 【12】Given an array of integers, remove the smallest value. Do not mutate the original array/list. If there are multiple elements with the same value, remove the one with a lower index. If you get an empty array/list, return an empty array/list.Don’t change the order of the elements that are left.**==（即 给定一个整数数组，**删除最小的值**。不要改变原来的数组/列表。如果有**多个具有相同值的元素**，则**删除下标较低**的元素。如果你得到一个空数组/列表，返回一个空数组/列表。不要改变剩下元素的顺序。）==

**<mark>example</mark>**：

```
removeSmallest([1,2,3,4,5]) = [2,3,4,5]
removeSmallest([5,3,2,1,4]) = [5,3,2,4]
removeSmallest([2,2,1,2,1]) = [2,2,2,1] 
```

**<mark>思路：</mark>**

*   先检查数组长度是否为0，如果为空数组，则返回空数组；
*   否则寻找数组中的最小元素；
*   如果只有一个直接删除；如果有多个，则找到下标最低的元素删除。

**<mark>solution：</mark>**

```
<script type="text/javascript"> function removeSmallest(numbers) {

			var length = numbers.length;

			if(length!=0){

				var min = Math.min(...numbers);

				var index = [];
				for(var i=0;i<length;i++){
					if(min == numbers[i]){
						index.push(i);
					}
				}

				var indexMin = Math.min(...index);

				numbers.splice(indexMin,1);

				return numbers;
			}else{
				return [];
			}
		}

		console.log(removeSmallest([1,2,3,4,5]));
		console.log(removeSmallest([2,2,1,2,1]) ); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>