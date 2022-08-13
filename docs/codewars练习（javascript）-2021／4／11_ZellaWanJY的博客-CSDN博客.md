<!--yml
category: codewars
date: 2022-08-13 11:46:25
-->

# codewars练习（javascript）-2021/4/11_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/115591746?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-115591746.nonecase](https://blog.csdn.net/FemaleHacker/article/details/115591746?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-115591746.nonecase)

## codewars-js练习

### 2021/4/11

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Thinkful - Logic Drills: Traffic light】

您需要一个函数来处理从绿色、到黄色、再到红色，然后再到绿色的每次变化。

**<mark>example</mark>**：

```
update_light('green') should return 'yellow' 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function updateLight(current) {

		if(current == 'green') return 'yellow';
		else if(current == 'yellow') return 'red';
		else  return 'green';
	}

	console.log(updateLight("green"));
	console.log(updateLight("yellow"));
	console.log(updateLight("red")); </script> 
```

#### 【2】<8kyu>【Powers of 2】

**<mark>example</mark>**：

```
n = 0  ==> [1]        
n = 1  ==> [1, 2]     
n = 2  ==> [1, 2, 4] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function powersOfTwo(n){

		var result = [];
		for(var i=0;i<=n;i++){
			result.push(Math.pow(2,i));
		}
		return result
	}

	console.log(powersOfTwo(0));
	console.log(powersOfTwo(1));
	console.log(powersOfTwo(4)); </script> 
```

#### 【3】<6kyu>【All Star Code Challenge #15】

该函数接受一个字符串参数，并返回一个字符串数组，将输入字符串中的每个字母旋转到末尾。

**<mark>example</mark>**：

```
rotate("Hello") 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function rotate(str){

		var arr = str.split('')
		var result = [];
		for(var i=0;i<arr.length;i++){
			temp = arr.shift();
			arr.push(temp)
			result.push(arr.join(''))
		}
		return result
	}

	console.log(rotate("Hello")); </script> 
```