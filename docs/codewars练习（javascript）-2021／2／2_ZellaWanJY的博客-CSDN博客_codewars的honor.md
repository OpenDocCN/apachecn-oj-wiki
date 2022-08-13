<!--yml
category: codewars
date: 2022-08-13 11:39:25
-->

# codewars练习（javascript）-2021/2/2_ZellaWanJY的博客-CSDN博客_codewars的honor

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113546742?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-25-113546742-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/113546742?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-25-113546742-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/2/2

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【You’re a square!】

Given an integral number, determine if it’s a [square number](https://en.wikipedia.org/wiki/Square_number):

**<mark>example</mark>**：

```
-1  =>  false
 0  =>  true
 3  =>  false
 4  =>  true
25  =>  true
26  =>  false 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> var isSquare = function(n){
 			console.log(n);
 			let i = 0;
 			if(n!=0){
 				while (n > i * i) {
					i++;
				}
				return i * i === n;
 			}
 			return true;
 		}

		console.log(isSquare(-1));
		console.log(isSquare(25));
		console.log(isSquare(0)); </script> 
```

#### 【2】<7kyu>【Find the next perfect square!】

You might know some pretty large perfect squares. But what about the NEXT one?

Complete the `findNextSquare` method that finds the next integral perfect square after the one passed as a parameter. Recall that an integral perfect square is an integer n such that sqrt(n) is also an integer.

If the parameter is itself not a perfect square then `-1` should be returned. You may assume the parameter is positive.

**找下一个完全平方数**

**<mark>example</mark>**：

```
findNextSquare(121) --> returns 144
findNextSquare(625) --> returns 676
findNextSquare(114) --> returns -1 since 114 is not a perfect 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function findNextSquare(sq) {

			for(var i=0;i>-1;i++){
				var square = i*i;
        		if(square==sq){

        			return (i+1)*(i+1);
        		}else if(square>sq){
        			return -1;
        		} 
			}
 		}

		console.log(findNextSquare(121));
		console.log(findNextSquare(625));
		console.log(findNextSquare(114)); </script> 
```

#### 【3】<7kyu>【Predict your age!】

In honor of my grandfather’s memory we will write a function using his formula!

*   Take a list of ages when each of your great-grandparent died.
*   Multiply each number by itself.
*   Add them all together.
*   Take the square root of the result.
*   Divide by two.

**列出你曾祖父去世时的年龄。把每个数单独乘起来。把它们加在一起。对结果开平方根。除以2。**

**<mark>example</mark>**：

```
predictAge(65, 60, 75, 55, 60, 63, 64, 45) === 86 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function predictAge(age1,age2,age3,age4,age5,age6,age7,age8){
 			let arr = [age1,age2,age3,age4,age5,age6,age7,age8];
 			console.log(arr);
 			let sum = 0;
 			for(var i=0;i<arr.length;i++){
 				sum +=(arr[i] * arr[i]);
 			}
 			return Math.floor(Math.sqrt(sum)/2);
 		}

		console.log(predictAge(65, 60, 75, 55, 60, 63, 64, 45)); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>