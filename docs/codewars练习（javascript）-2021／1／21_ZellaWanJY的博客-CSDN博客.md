<!--yml
category: codewars
date: 2022-08-13 11:46:40
-->

# codewars练习（javascript）-2021/1/21_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/112972003?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-112972003.nonecase](https://blog.csdn.net/FemaleHacker/article/details/112972003?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-112972003.nonecase)

## codewars-js练习

### 2021/1/21

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【N-th Power】

You are given an array with positive numbers and a non-negative number N. You should find the N-th power of the element in the array with the index N. If N is outside of the array, then return -1\. Don’t forget that the first element has the index 0.

**<mark>example</mark>**：

```
array = [1, 2, 3, 4] and N = 2, then the result is 3^2 == 9;
array = [1, 2, 3] and N = 3, but N is outside of the array, so the result is -1. 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> function index(array, n){
			var length = array.length;
			if(n>=length){
				return -1;
			}else{
				for(var i=0;i<length;i++){
					if(i == n){
						return Math.pow(array[i],n);
					}
				}
			}
		}

		console.log(index([1, 2, 3, 4],2));
		console.log(index([1, 2],3)); </script> 
```

#### 【2】<8kyu>【Aspect Ratio Cropping - Part 1】

Write a function that accepts arbitrary X and Y resolutions and converts them into resolutions with a 16:9 aspect ratio that maintain equal height. Round your answers up to the nearest integer.

**<mark>example</mark>**：

```
aspectRatio(640, 480)
aspectRatio(960,720) 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> function aspectRatio(x,y){
 			var width = Math.ceil(y*16/9);
 			var result = [width,y];

 			return result;
		}

		console.log(aspectRatio(640, 480));
		console.log(aspectRatio(960,720)); </script> 
```

#### 【3】<8kyu>【Grasshopper - Basic Function Fixer】

I created this function to add five to any number that was passed in to it and return the new value. It doesn’t throw any errors but it returns the wrong number.

**<mark>solution：</mark>**

```
<script type="text/javascript"> function addFive(num) {
			var total = num + 5;
			return total
		}

		console.log(addFive(5)); </script> 
```

#### 【4】<8kyu>【Convert a Boolean to a String】

Implement a function which convert the given boolean value into its string representation.

**<mark>example</mark>**：

```
booleanToString(true) 
```

**<mark>solution：</mark>**

```
<script type="text/javascript"> function booleanToString(b){
			if(typeof b == 'boolean'){

				return String(b);
			}
		}

		console.log(booleanToString(true)); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>