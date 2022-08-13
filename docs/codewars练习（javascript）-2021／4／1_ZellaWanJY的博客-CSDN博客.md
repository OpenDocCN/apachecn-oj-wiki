<!--yml
category: codewars
date: 2022-08-13 11:40:35
-->

# codewars练习（javascript）-2021/4/1_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/115385390?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-23-115385390-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/115385390?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-23-115385390-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/4/1

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Thinkful - String Drills: Repeater】

**<mark>example</mark>**：

```
Repeater.repeat("a", 5) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function repeater(string, n){
		var str = string;
		for(var i=0;i<n-1;i++){
			str = str + string;
		}
		return str;
	}

  	console.log(repeater('a', 5));
	console.log(repeater('Na', 16));
	console.log(repeater('Wub ', 6)); </script> 
```

#### 【2】<7kyu>【Char Code Calculation】

返回差值

**<mark>example</mark>**：

```
'ABC' --> 'A' = 65, 'B' = 66, 'C' = 67 --> 656667
total1 = 656667
              ^
total2 = 656661
              ^
 (6 + 5 + 6 + 6 + 6 + 7)
- (6 + 5 + 6 + 6 + 6 + 1)
-------------------------
                       6 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function calc(x){

		var arr = x.split('');
		var temp = [];
		for(var i = 0;i<arr.length;i++){
			temp.push(arr[i].charCodeAt())
		}
		var str = temp.join('');
		var str1 = JSON.parse(JSON.stringify(str));
		str = str.replace(/[7]/g,1);

		var a = str.split('').reduce((total,cur)=>parseInt(total)+parseInt(cur),0);
		var b = str1.split('').reduce((total,cur)=>parseInt(total)+parseInt(cur),0);
		return b-a;
	}

  	console.log(calc('ABC'));
	console.log(calc('abcdef'));
	console.log(calc('ifkhchlhfd'));
	console.log(calc('aaaaaddddr'));
	console.log(calc('abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ')); </script> 
```