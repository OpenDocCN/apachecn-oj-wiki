<!--yml
category: codewars
date: 2022-08-13 11:49:21
-->

# codewars第四篇（8kyu）Is your period late?_弥玥的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_37629509/article/details/103628138?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-103628138.nonecase](https://blog.csdn.net/qq_37629509/article/details/103628138?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-103628138.nonecase)

**题目：**
In this kata, we will make a function to test whether a period is late.

Our function will take three parameters:

last - The Date object with the date of the last period

today - The Date object with the date of the check

cycleLength - Integer representing the length of the cycle in days

If the today is later from last than the cycleLength, the function should return true. We consider it to be late if the number of passed days is larger than the cycleLength. Otherwise return false.
**较好的解答：**

```
function periodIsLate(last, today, cycleLength)
{
  return (today-last)/86400000>cycleLength
} 
```

```
var _MS_PER_DAY = 1000 * 60 * 60 * 24;

function periodIsLate(last, today, cycleLength)
{
  return Math.floor((today - last) / _MS_PER_DAY) > cycleLength;
} 
```

**自己的解答：**

```
function periodIsLate(last, today, cycleLength)
{
  let month = today.getMonth()- last.getMonth();
  if(month){
    month = month * new Date(today.getYear(), today.getMonth(), 0).getDate()
  }
  return today.getDate() - last.getDate() + month > cycleLength ? true : false ;
} 
```