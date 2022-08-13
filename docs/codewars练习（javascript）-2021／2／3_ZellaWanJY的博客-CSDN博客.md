<!--yml
category: codewars
date: 2022-08-13 11:36:48
-->

# codewars练习（javascript）-2021/2/3_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113578907?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-113578907.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/113578907?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-113578907.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/2/3

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Gauß needs help! (Sums of a lot of numbers).】

求和

**<mark>example</mark>**：

```
f(n=100) 
f('n')
f(3.14)
f(-10)
f(0) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function f(n){
 			console.log(n);
 			if(typeof n == 'number' && n % 1 ==0 && n > 0){
 				var sum =0;
 				for(var i=0;i<=n;i++){
 					sum +=i;
 				}
 				return sum;
 			}
 			return false;	
 		}

		console.log(f(100));
		console.log(f('n'));
		console.log(f(3.14)); </script> 
```

#### 【2】<7kyu>【Sum of odd numbers】

Given the triangle of consecutive odd numbers:

```
 1
          3     5
       7     9    11
   13    15    17    19
21    23    25    27    29
... 
```

Calculate the row sums of this triangle from the row index (starting at index 1) e.g.:

**<mark>example</mark>**：

```
rowSumOddNumbers(1); 
rowSumOddNumbers(2); 
rowSumOddNumbers(42); 
```

<mark>**思路**</mark>

| n | 第一个数 | 该行总数 | 最后一个数 |
| :-: | :-: | :-: | --- |
| 1 | 1 | 1 | 1 |
| 2 | 3 | 2 | 5 |
| 3 | 7 | 3 | 11 |
| 4 | 13 | 4 | 19 |
| 5 | 21 | 5 | 29 |
| … | n(n-1)+1 (n>=2) | … | n(n-1)+1+(n-1)2=(n-1)(n+2)+1 |

根据n确定第一个数和该行最后一个数，从而计算。

<mark>**solution**</mark>

```
<script type="text/javascript"> function rowSumOddNumbers(n) {

 			var one = n * (n-1) + 1;
 			var last = (n-1) * (n+2) + 1;

 			var sum = 0;
 			for(var i=one;i<=last;i=i+2){
 				sum +=i;
 			}
 			return sum;
 		}

		console.log(rowSumOddNumbers(1)); 
		console.log(rowSumOddNumbers(2)); 
		console.log(rowSumOddNumbers(42)); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>