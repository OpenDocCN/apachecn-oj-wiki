<!--yml
category: codewars
date: 2022-08-13 11:27:58
-->

# codewars练习（javascript）-2021/2/15_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113813707?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-113813707.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/113813707?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-113813707.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/2/15

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### *【1】*<6kyu>【N smallest elements in original order (performance edition)】

You will be given an array of integers, very few of which are unique, and a number `n`. You have to extract `n` smallest elements out of the array **preserving their original order**.

你将得到一个整数数组，其中很少是唯一的，以及一个数字n。你必须从数组中提取出n个最小的元素，保持它们原来的顺序。

**<mark>example</mark>**：

```
numbers = [1, 2, 3, 4, 5]
n = 3
result = [1, 2, 3]

numbers = [5, 4, 3, 2, 1]
n = 3
result = [3, 2, 1]

numbers = [1, 2, 4, 1, 2]
n = 3
result = [1, 2, 1] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function performantSmallest(arr, n) {
  			let d = Array(arr.length+1).fill(0);
  			console.log(d);
  			for(let x of arr) d[x]++;
  			console.log(d);

 			let s = 0;
  			for(let i = 0; i < d.length; ++i) {
    			if(s < n) {
     			s += d[i];
      			if(s > n) d[i] -= s - n;
    			} else {
      				d[i] = 0;
   				}
  			}
  			let r = [];
  			for(let x of arr)
    			if(d[x] > 0) {
      				d[x]--;
      				r.push(x);
      				if(r.length == n) break;
    			}
 			return r;
		}

		console.log(performantSmallest([5,4,3,2,1],3)); </script> 
```

<mark>以上为大佬解法。</mark>