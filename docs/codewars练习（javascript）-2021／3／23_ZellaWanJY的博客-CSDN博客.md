<!--yml
category: codewars
date: 2022-08-13 11:47:01
-->

# codewars练习（javascript）-2021/3/23_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/115110092?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-115110092.nonecase](https://blog.csdn.net/FemaleHacker/article/details/115110092?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-115110092.nonecase)

## codewars-js练习

### 2021/3/23

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Fake Binary】

Given a string of digits, you should replace any digit below 5 with ‘0’ and any digit 5 and above with ‘1’. Return the resulting string.

**用’0’代替5以下的数字，用’1’代替5以上的数字。**

**<mark>example</mark>**：

```
'45385593107843568' 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function fakeBin(x){

		x = x.replace(/[1-4]/g,'0')
		return x.replace(/[^0-4]/g,'1')
	}

    console.log(fakeBin('45385593107843568')); </script> 
```

#### 【2】<8kyu>【My head is at the wrong end!】

你会得到一个有三个值的数组(tail, body, head)。你的工作是重新安排排列，使动物是正确的方式(头，身体，尾巴)。

**<mark>example</mark>**：

```
["tail", "body", "head"]), ["head", "body", "tail"]);
["ground", "rainbow", "sky"]), ["sky", "rainbow", "ground"]); 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function fixTheMeerkat(arr) {
		return arr.reverse()
	}

    console.log(fixTheMeerkat(["tail", "body", "head"]));
	console.log(fixTheMeerkat(["tails", "body", "heads"]));
	console.log(fixTheMeerkat(["bottom", "middle", "top"]));
	console.log(fixTheMeerkat(["lower legs", "torso", "upper legs"]));
	console.log(fixTheMeerkat(["ground", "rainbow", "sky"])); </script> 
```

#### 【3】<5kyu>【Maximum subarray sum】

The maximum sum subarray problem consists in finding the maximum sum of a contiguous subsequence in an array or list of integers

**<mark>example</mark>**：

```
maxSequence([-2, 1, -3, 4, -1, 2, 1, -5, 4]) 
```

**用`for`循环遍历数组`arr`，每次取到一个元素后，加到`maxTemp`中，然后判断`maxTemp`，若小于`0`，则将`maxTemp`设置为`0`，否则不变。然后去`maxTemp`和`maxRes`的最大值赋给`maxRes`用于返回。**

<mark>**solution**</mark>

```
<script type="text/javascript"> var maxSequence = function(arr){

		if(arr.length ==0)return 0;
		var maxTemp = 0;
  		var max = 0;
  		for(var k of arr){
    		maxTemp += k;
    		if(maxTemp <0)maxTemp = 0;
    		max = max >= maxTemp? max : maxTemp;
    	}
    	return max
	}

    console.log(maxSequence([]));
	console.log(maxSequence([-2, 1, -3, 4, -1, 2, 1, -5, 4])); </script> 
```