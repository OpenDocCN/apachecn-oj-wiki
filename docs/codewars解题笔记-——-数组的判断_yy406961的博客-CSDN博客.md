<!--yml
category: codewars
date: 2022-08-13 11:43:26
-->

# codewars解题笔记 —— 数组的判断_yy406961的博客-CSDN博客

> 来源：[https://blog.csdn.net/yy406961/article/details/78045191?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-78045191.nonecase](https://blog.csdn.net/yy406961/article/details/78045191?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-78045191.nonecase)

题目：

You get an array of arrays.
If you sort the arrays by their length, you will see, that their length-values are consecutive.
But one array is missing!

You have to write a method, that return the length of the missing array.

Example:
[[1, 2], [4, 5, 1, 1], [1], [5, 6, 7, 8, 9]] --> 3

If the array of arrays is null/nil or empty, the method should return 0.

When an array in the array is null or empty, the method should return 0 too!
There will always be a missing element and its length will be always between the given arrays. 

数组中是长度连续的几个数组，缺失了中间的某一个，找到缺失的那一个的长度是多少，如果传的是空数组，返回0，如果数组中有长度为0的数组，返回0

我的答案：

```
function getLengthOfMissingArray(arrayOfArrays) {
      let a = null
      if(arrayOfArrays === '' || !arrayOfArrays) {
        a = 0
      }else if(arrayOfArrays.length === 0){
	a = 0
      } else {
	let arr = []
	arrayOfArrays.map(item => {
            if(item){
              arr.push(item.length)
            }else {
              a = 0
            }
	})
	arr.sort(sortNumber)
        console.log(arr)
        if (arr[0] === 0) {
          a = 0
        }else {
          arr.forEach((item, index) => {
  	  if(item+1 !== arr[index+1] && arr[index+1]){
  	  a = item+1
  	      }  
  	   })
        }
      }
      console.log(a)
      return a 
}
function sortNumber(a,b){
  return a - b
}
```

票数最高的答案

```
function getLengthOfMissingArray(arrayOfArrays) {
  const lengths = (arrayOfArrays || [])
    .map(a => a ? a.length : 0)
    .sort((a, b) => a - b)

  if (lengths.includes(0)) {
    return 0
  }

  for (let i = 0; i < lengths.length - 1; i++) {
    if (lengths[i] + 1 !== lengths[i + 1]) {
      return lengths[i] + 1
    }
  }

  return 0
}
```

思考：

1、清晰的解题思路很重要

2、多用链式结构，更简洁高效

3、记住一些常用的代码，比如这个例子中的排序

**arr.sort((a, b) => a-b)**

```
10,5,40,25,1000,1  =>  1,5,10,25,40,1000
```