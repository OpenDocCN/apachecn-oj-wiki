<!--yml
category: codewars
date: 2022-08-13 11:48:44
-->

# codewars练习（javascript）-2021/2/4_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113662929?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-113662929.nonecase](https://blog.csdn.net/FemaleHacker/article/details/113662929?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-113662929.nonecase)

## codewars-js练习

### 2021/2/4

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Sorted? yes? no? how?】

Complete the method which accepts an array of integers, and returns one of the following:

*   `"yes, ascending"` - if the numbers in the array are sorted in an ascending order
*   `"yes, descending"` - if the numbers in the array are sorted in a descending order
*   `"no"` - otherwise

**<mark>example</mark>**：

```
it("[1, 2]", function() {
    Test.assertEquals(isSortedAndHow([1, 2]), 'yes, ascending');
  });
 it("[15, 7, 3, -8]", function() {
    Test.assertEquals(isSortedAndHow([15, 7, 3, -8]), 'yes, descending');
  }); 
  it("[4, 2, 30]", function() {
    Test.assertEquals(isSortedAndHow([4, 2, 30]), 'no');
  }); 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function isSortedAndHow(array) {

 			var array1 = JSON.parse(JSON.stringify(array));
 			var array2 = JSON.parse(JSON.stringify(array));
 			var array3 = JSON.parse(JSON.stringify(array));

 			var arr = array.sort((a,b)=>{return a-b});

 			var arr1 = array3.sort((a,b)=>{return b-a});

 			if(arr.toString() == array1.toString()){
 				return 'yes, ascending';
 			}else if(arr1.toString() == array2.toString()){
 				return 'yes, descending';
 			}else{
 				return 'no';
 			}		
 		}

		console.log(isSortedAndHow([1,2])); 
		console.log(isSortedAndHow([15, 7, 3, -8])); 
		console.log(isSortedAndHow([4, 2, 30])); </script> 
```

#### 【2】<7kyu>【Sort Numbers】

Finish the solution so that it sorts the passed in array of numbers. If the function passes in an empty array or null/nil value then it should return an empty array.

**<mark>example</mark>**：

```
solution([1, 2, 10, 50, 5]); 
solution(null); 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function solution(nums){

 			return (nums || []).sort((a, b)=>{return a - b});
 		}

		console.log(solution([1,2,10,50,5])); 
		console.log(solution(null)); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>