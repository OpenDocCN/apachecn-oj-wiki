<!--yml
category: codewars
date: 2022-08-13 11:39:04
-->

# codewars练习（javascript）-2021/4/14_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/115690382?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-15-115690382-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/115690382?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-15-115690382-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/4/14

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Do you speak “English”?】

<mark>**solution**</mark>

```
<script type="text/javascript"> function spEng(sentence){
		console.log(sentence)
		return (/english/i).test(sentence)
	}

	console.log(spEng("english"));
	console.log(spEng("egnlish")); </script> 
```

#### 【2】<7kyu>【Filter Long Words】

返回一个包含所有长于n的单词的列表。

**<mark>example</mark>**：

```
filterLongWords("The quick brown fox jumps over the lazy dog", 4) = ['quick', 'brown', 'jumps'] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function filterLongWords(sentence, n) {
		console.log(sentence,n)
		var arr = sentence.split(' ');
		var result = [];
		for(var i=0;i<arr.length;i++){
			if(arr[i].length >n){
				result.push(arr[i]);
			}
		}
		return result
	} </script> 
```

#### 【3】<6kyu>【English beggars】

给定一组值和一个乞丐,你应该返回一个数组,每个乞丐带回家的总和,假设他们都进行有规律的转动,从第一个到最后一个。

**<mark>example</mark>**：

```
For example: [1,2,3,4,5] for 2 beggars will return a result of [9,6], as the first one takes [1,3,5], the second collects [2,4].
The same array with 3 beggars would have in turn have produced a better out come for the second beggar: [5,7,3], as they will respectively take [1,4], [2,5] and [3]. 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function beggars(values, n){
		console.log(values,n)
		var outputValues = [];
		for (var i = 0; i < n; i++) {
			var sum = 0;
			for (var j = i; j < values.length; j += n) {
		  		sum += values[j];
			}
			outputValues.push(sum);
		}
		return outputValues;
	}

	console.log(beggars([1,2,3,4,5],1));
	console.log(beggars([1,2,3,4,5],2));
	console.log(beggars([1,2,3,4,5],3)); </script> 
```

#### 【4】<8kyu>【Drink about】

*   Children under 14 old.
*   Teens under 18 old.
*   Young under 21 old.
*   Adults have 21 or more.

**<mark>example</mark>**：

```
13 --> "drink toddy"
17 --> "drink coke"
18 --> "drink beer"
20 --> "drink beer"
30 --> "drink whisky" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function peopleWithAgeDrink(old) {
		console.log(old)
		if(old<14)return 'drink toddy';
		else if(old<18 && old>=14) return "drink coke";
		else if(old<21 && old>=18) return "drink beer";
		else return "drink whisky";
	}

	console.log(peopleWithAgeDrink(22)); </script> 
```

#### 【5】<8kyu>【Keep up the hoop】

-If Alex gets 10 or more hoops, return the string “Great, now move on to tricks”.

-If he doesn’t get 10 hoops, return the string “Keep at it until you get it”.

<mark>**solution**</mark>

```
<script type="text/javascript"> function hoopCount (n) {
		console.log(n)
		if(n<10) return "Keep at it until you get it" ;
		else return "Great, now move on to tricks"
	}

	console.log(hoopCount(3));
	console.log(hoopCount(11)); </script> 
```

#### 【6】<8kyu>【Holiday VIII - Duty Free】

**<mark>example</mark>**：

```
12, 50, 1000 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function dutyFree(normPrice, discount, hol){
		console.log(normPrice,discount,hol)
		return Math.floor(hol / (normPrice * (discount/100)))
	}

	console.log(dutyFree(12, 50, 1000));
	console.log(dutyFree(17, 10, 500));
	console.log(dutyFree(24, 35, 3000)); </script> 
```