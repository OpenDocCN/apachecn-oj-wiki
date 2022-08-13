<!--yml
category: codewars
date: 2022-08-13 11:30:14
-->

# codewars练习（javascript）-2021/3/22_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/115084149?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-115084149.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/115084149?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-115084149.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/3/22

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Get Nth Even Number】

**<mark>example</mark>**：

```
nthEven(1) 
nthEven(3) 

nthEven(100) 
nthEven(1298734) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function nthEven(n){

		return 2*n-2;
	}

    console.log(nthEven(1));
	console.log(nthEven(3));
	console.log(nthEven(100)); 
	console.log(nthEven(1298734)); </script> 
```

#### 【2】<8kyu>【What is between?】

**<mark>example</mark>**：

```
a = 1
b = 4
--> [1, 2, 3, 4] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function between(a, b) {

		var result = [];
		for(var i=a;i<=b;i++)result.push(i);
		return result
	}

    console.log(between(1,4)); </script> 
```

#### 【3】<8kyu>【DNA to RNA Conversion】

即将T全部改为U

**<mark>example</mark>**：

```
"GCAT"  =>  "GCAU" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function DNAtoRNA(dna) {

		return dna.replace(/[T]/g,'U')
	}

    console.log(DNAtoRNA("TTTT"));
	console.log(DNAtoRNA("GCAT"));
	console.log(DNAtoRNA("GACCGCCGCC")); </script> 
```