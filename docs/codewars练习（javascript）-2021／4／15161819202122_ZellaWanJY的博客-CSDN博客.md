<!--yml
category: codewars
date: 2022-08-13 11:33:05
-->

# codewars练习（javascript）-2021/4/15161819202122_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/115733405?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036053316781667833427%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036053316781667833427&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-21-115733405-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/115733405?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036053316781667833427%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036053316781667833427&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-21-115733405-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/4/15

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Drone Fly-By】

**<mark>example</mark>**：

```
'xxxxxx', '====T'
'xxxxxxxxx', '==T'
'xxxxxxxxxxxxxxx', '=========T' 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function flyBy(lamps, drone){

		var len = drone.length;
		var str = lamps.substring(0,len).replace(/x/g,'o');;
		return str + lamps.substring(len,);
	} </script> 
```

#### 【2】<8kyu>【Abbreviate a Two Word Name】

**<mark>example</mark>**：

```
Sam Harris` => `S.H
Patrick Feeney` => `P.F 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function abbrevName(name){

		var arr = name.split(' ');
		return arr[0].substring(0,1).toUpperCase() + '.' + arr[1].substring(0,1).toUpperCase() ;
	} </script> 
```

#### 【3】<7kyu>【Substituting Variables Into Strings: Padded Numbers】

**<mark>example</mark>**：

```
solution(5) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function solution(value){
		console.log(value)
		if(value == 0)return "Value is 00000";
		var len = 5 - (value.toString().split('').length);
		var arr = [];
		for(var i=0;i<len;i++){
			arr.push(0)
		}
		arr.push(value)
		return 'Value is ' + arr.join('');

		return "Value is " + ("00000" + value).slice(-5);

	}

	console.log(solution(5));
	console.log(solution(1204));
	console.log(solution(0)); </script> 
```

```
<script type="text/javascript">
	function solution(value){
		console.log(value)
		return "Value is " + ("00000" + value).slice(-5);

	}

	console.log(solution(5));
	console.log(solution(1204));
	console.log(solution(0));
</script> 
```

### 2021/4/16

#### 【1】<7kyu>【JavaScript Array Filter】

**<mark>example</mark>**：

```
getEvenNumbers([2,4,5,6]) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function check(numbers){
		return (numbers % 2 ==0);
	}
	function getEvenNumbers(numbersArray){

		return  numbersArray.filter(check);
	}

	console.log(getEvenNumbers([1,2,3,6,8,10]));
	console.log(getEvenNumbers([1,2]));
	console.log(getEvenNumbers([12,14,15]));
	console.log(getEvenNumbers([13,15])); </script> 
```

#### *【2】<6kyu>【Point in Polygon】*

测试一个点是否在多边形内。

该多边形将是多边形顶点的点数组。数组中的最后一个点连接回第一个点。

**<mark>example</mark>**：

```
[[-5, -5], [5, -5], [0, 5]]      [0,0] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function pointInPoly(poly, point) {
		let inside = false;

		const px = point[0];
		const py = point[1];

		for (var start = 0, end = poly.length - 1; start < poly.length; end = start++) {    
			const x1 = poly[start][0];
			const y1 = poly[start][1];    
			const x2 = poly[end][0];
			const y2 = poly[end][1];    
			const dx = x2 - x1;
			const dy = y2 - y1;
			const t = (py - y1) / dy;    

			if (y1 > py != y2 > py)      
			  if (dx * t + x1 >= px)     
			    inside = !inside;        
		}
		return inside;
}

	var poly = [[-5, -5], [5, -5],[5, 5], [-5, 5]];
	console.log(pointInPoly(poly, [-6,0]));
	console.log(pointInPoly(poly, [1,1])); </script> 
```

### 2021/4/18

#### 【1】<7kyu>【Spraying trees】

There are five workers : James,John,Robert,Michael and William.They work one by one and on weekends they rest. Order is same as in the description(James works on mondays,John works on tuesdays and so on).

Your function should return string like this : `'It is (weekday) today, (name), you have to work, you must spray (number) trees and you need (x) dollars to buy liquid'`

**<mark>example</mark>**：

```
task('Monday',15,2) -> 'It is Monday today, James, you have to work, you must spray 15 trees and you need 30 dollars to buy liquid' 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function task(w, n, c) {
		console.log(w,n,c)
		var map = {'Monday':'James','Tuesday':'John','Wednesday':'Robert','Thursday':'Michael','Friday':'William'};
		var money = n*c;
		return 'It is '+ w +' today, '+ map[w] +', you have to work, you must spray '+ n +' trees and you need '+money+' dollars to buy liquid'
	}

	console.log(task('Wednesday',10,2));
	console.log(task('Monday',4,3));
	console.log(task('Friday',5,4)); </script> 
```

### 2021/4/19

#### 【1】<7kyu>【Harvest Festival】

种子(字符串)-确定植物产生的花的类型。

水(整数)-每个单位的水延伸的部分茎之间的花。它也给出了茎+花簇应该重复的次数

fert(整数)-每单位肥料增加花的数量，分组成簇

温度(整数)——如果给定的温度在20°C到30°C之间，则植物正常生长;否则，除茎端部的一朵花外，所有花都死亡。

**<mark>example</mark>**：

```
plant("@", 3, 3, 25) => "---@@@---@@@---@@@"

plant("$", 4, 2, 30) => "----$$----$$----$$----$$"

plant("&", 1, 5, 20) => "-&&&&&"

plant("^", 3, 3, 35) => "---------^" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function plant(seed, water, fert, temp){
		console.log(seed,water,fert,temp)
		var temp1=[];
		var temp2=[];
		for(var i=0;i<water;i++)temp1.push('-');
		for(var j=0;j<fert;j++)temp2.push(seed);
		var str = temp1.join('') + temp2.join('');
		var result = [];
		if(temp<20 || temp>30){
			for(var i=0;i<water;i++){
				result.push(temp1.join(''));
			}
			return result.join('') + seed;
		} </script> 
```

```
<script type="text/javascript"> function plant(seed, water, fert, temp){
		let arr = [];
		for(let i = 0; i < water; i += 1) {
			arr.push('-'.repeat(water));
			arr.push(seed.repeat(fert))
		}
		return temp < 20 || temp > 30 ? arr.join('').replace(/[^-]/g, '')+seed : arr.join('');
	} </script> 
```

### 2021/4/20

#### 【1】<7kyu>【Word to binary】

**<mark>example</mark>**：

```
'man' should return [ '01101101', '01100001', '01101110' ] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function wordToBin(str){
		console.log(str)

		var arr = str.split('');
		var result = [];
		for(var i=0;i<arr.length;i++){

			result.push('0'+arr[i].charCodeAt().toString(2))
		}
		return result
	}

	console.log(wordToBin('man'));
	console.log(wordToBin('AB'));
	console.log(wordToBin('wecking')); </script> 
```

#### 【2】<6kyu>【Meeting】

使这个字符串大写,按姓氏的字母顺序排序。

当姓氏相同时，按名字排序。客人的姓和名出现在由逗号分隔的圆括号中。

**<mark>example</mark>**：

```
"(CORWILL, ALFRED)(CORWILL, FRED)(CORWILL, RAPHAEL)(CORWILL, WILFRED)(TORNBULL, BARNEY)(TORNBULL, BETTY)(TORNBULL, BJON)" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function meeting(s) {
		console.log(s)
		let string = s.toUpperCase().split(';')
                .map(x => x.split(':').reverse().join(', '))
                .sort()
                .join(')(')
  		return '(' + string + ')'
	}

	console.log(meeting("Alexis:Wahl;John:Bell;Victoria:Schwarz;Abba:Dorny;Grace:Meta;Ann:Arno;Madison:STAN;Alex:Cornwell;Lewis:Kern;Megan:Stan;Alex:Korn")); </script> 
```

### 2021/4/21

#### 【1】<7kyu>【Valid Spacing】

有效空格的定义是单词之间的一个空格，不包含前导或尾随空格。

**<mark>example</mark>**：

```
'Hello world' = true
' Hello world' = false
'Hello world  ' = false
'Hello  world' = false
'Hello' = true

'Helloworld' = true 

'Helloworld ' = false
' ' = false
'' = true 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function validSpacing(s) {
		console.log(s)
		return s.replace(/\s+/g," ").trim()==s;
	}

	console.log(validSpacing('Hello world'));
	console.log(validSpacing('Hello'));
	console.log(validSpacing('Hello  world ')); </script> 
```

### 2021/4/22

#### 【1】<7kyu>【Evens times last】

给定一个整数序列，返回所有具有偶数下标的整数的和，再乘以最后一个下标的整数。

**<mark>example</mark>**：

```
evenLast([2, 3, 4, 5]), 30 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function evenLast(numbers) {
		console.log(numbers);
		var len = numbers.length;
		var sum = 0;
		if(len == 0)return 0;
		for(var i=0;i<numbers.length;i++){
			if(i%2==0){
				sum +=numbers[i];
			}
		}
		return sum * numbers[len-1]
	}

	console.log(evenLast([2, 3, 4, 5]));
	console.log(evenLast([])); </script> 
```