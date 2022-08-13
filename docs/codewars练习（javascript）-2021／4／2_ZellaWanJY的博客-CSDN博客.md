<!--yml
category: codewars
date: 2022-08-13 11:39:12
-->

# codewars练习（javascript）-2021/4/2_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/115391601?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-19-115391601-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/115391601?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-19-115391601-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/4/2

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Number of Divisions】

计算一个数字能被一个给定的数字除多少次。

**<mark>example</mark>**：

```
1. 100 / 2 = 50
2. 50 / 2 = 25
3. 25 / 2 = 12 remainder 1
4. 12 / 2 = 6
5. 6 / 2 = 3
6. 3 / 2 = 1 remainder 1 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> const divisions = (n, divisor) => {
		var count = 0;
		var d = n;
		while(Math.floor(d/divisor)!=0){
			count ++;
			d = d/divisor;
		}

		return count;
	};

  	console.log(divisions(6, 2));
	console.log(divisions(100, 2));
	console.log(divisions(9999, 3));
	console.log(divisions(2, 3));
	console.log(divisions(5, 5)); </script> 
```

#### 【2】<7kyu>【Palindromes Here and There】

一个包含回文数和非回文数的数组。回文数是一个顺序颠倒后仍然相同的数。例如，122不是回文数，但202是1。

您的任务是编写一个函数，返回一个只有1和0的数组，其中所有回文数字被替换为1，所有非回文数字被替换为0。

**<mark>example</mark>**：

```
[101, 2, 85, 33, 14014]  ==>  [1, 1, 0, 1, 0]
[45, 21, 303, 56]        ==>  [0, 0, 1, 0] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function convertPalindromes(numbers) {

		var arr = [];
		for(var i=0;i<numbers.length;i++){
			if(numbers[i].toString().split('').reverse().join('') == numbers[i].toString())arr.push(1);
			else arr.push(0);
		}
		return arr
	};

  	console.log(convertPalindromes([101, 2, 85, 33, 14014]));
  	console.log(convertPalindromes([45, 21, 303, 56] )); </script> 
```

#### 【3】<6kyu>【Valid string】

给定一个有效的单词序列和一个字符串。测试字符串是否由数组中的一个或多个单词组成。

测试字符串是否可以通过连接字典中的单词完全形成。

**<mark>example</mark>**：

```
string[] dictionary = ["code", "wars"]; 

string s = "codewars"; 

string s1 = "codewar"; 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> var validWord = function(dictionary, word) {
		console.log(dictionary,word)
		reg = new RegExp('^(' + dictionary.join('|') + ')+$');
  		return reg.test(word);

	};

  	console.log(validWord(['code', 'wars'], 'code')); </script> 
```