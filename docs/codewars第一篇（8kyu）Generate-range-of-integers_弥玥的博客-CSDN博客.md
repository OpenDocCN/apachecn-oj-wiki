<!--yml
category: codewars
date: 2022-08-13 11:44:12
-->

# codewars第一篇（8kyu）Generate range of integers_弥玥的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_37629509/article/details/103611109?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-103611109.nonecase](https://blog.csdn.net/qq_37629509/article/details/103611109?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-103611109.nonecase)

**题目：**
Implement a function named generateRange(min, max, step), which takes three arguments and generates a range of integers from min to max, with the step. The first integer is the minimum value, the second is the maximum of the range and the third is the step. (min < max)
**Task：**
Implement a function named

```
generateRange(2, 10, 2) // should return array of [2,4,6,8,10]
generateRange(1, 10, 3) // should return array of [1,4,7,10] 
```

**Note：**

*   min < max
*   step > 0
*   the range does not HAVE to include max (depending on the step)

**个人觉得最佳解答：**

```
function generateRange(min, max, step){
  let arr = [];
  for (let i=min; i<=max; i += step) {
    arr.push(i);
  }
  return arr;
} 
```

**自己的解答：**

```
function generateRange(min, max, step){
  let arr = [];
  let rel = min + step;
  let mid = [rel];
 while (rel <= max - step) {
    rel = rel + step;
    mid.push(rel);
  }
  arr.push(min, ...mid);
  return arr;
} 
```