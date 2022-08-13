<!--yml
category: codewars
date: 2022-08-13 11:35:26
-->

# codewars练习（javascript）-2021/2/7_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113737060?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-113737060.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/113737060?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-113737060.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/2/7

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### *【1】*<5kyu>【Common Denominators】

**<mark>example</mark>**：

```
convertFracs [(1, 2), (1, 3), (1, 4)] `shouldBe` [(6, 12), (4, 12), (3, 12)] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function convertFrac(lst){
  		var gcd = (a, b) => b ? gcd(b, a % b) : a;
  		var lcm = lst.reduce((res, i) => res * i[1] / gcd(res, i[1]), 1);
  		return lst.reduce((res, i) => res + '('+ lcm / i[1] * i[0] +','+ lcm +')', '');
}

		var lst = [ [1, 2], [1, 3], [1, 4] ]
		console.log(convertFrac(lst)); </script> 
```

#### 【2】<6kyu>【Find the odd int】

Given an array of integers, find the one that appears an odd number of times.

There will always be only one integer that appears an odd number of times.

**给定一个整数数组，找出出现奇数次的整数。**

**<mark>example</mark>**：

```
[20,1,-1,2,-2,3,3,5,5,1,2,4,20,4,-1,-2,5]
[1,1,2,-2,5,2,4,4,-1,-2,5]
[10], 10
[5,4,3,2,1,5,4,3,2,10,10], 1 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function findOdd(A) {

 			var map = {};
 			for(var i=0;i<A.length;i++){

 				var key = A[i];

 				if(map[key]){
 					map[key] ++;
 				}else{
 					map[key] =1;
 				}

 			}

 			for(var key in map){

 				if(map[key] %2 !=0){
 					return parseInt(key);
 				}
 			}
 		}

		console.log(findOdd([20,1,-1,2,-2,3,3,5,5,1,2,4,20,4,-1,-2,5]));
		console.log(findOdd([10])); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>