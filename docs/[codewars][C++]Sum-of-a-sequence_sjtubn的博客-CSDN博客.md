<!--yml
category: codewars
date: 2022-08-13 11:52:17
-->

# [codewars][C++]Sum of a sequence_sjtubn的博客-CSDN博客

> 来源：[https://blog.csdn.net/sjtubn/article/details/87879796?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-87879796.nonecase](https://blog.csdn.net/sjtubn/article/details/87879796?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-87879796.nonecase)

Your task is to make function, which returns the sum of a sequence of integers.

The sequence is defined by 3 non-negative values: **begin**, **end**, **step**.

If **begin** value is greater than the **end**, function should returns **0**

*Examples*

```
sequenceSum (2,2,2); // => 2
sequenceSum (2,6,2); // => 12 -> 2 + 4 + 6
sequenceSum (1,5,1); // => 15 -> 1 + 2 + 3 + 4 + 5
sequenceSum (1,5,3); // => 5 -> 1 + 4
```

 思路：这里除了遍历之外，只需要考虑step正负的情况即可

代码如下：

long long int sequence_sum(long long int begin_number, long long int end_number, long long step){
    //your code here
    long long int sum = 0;
    for (long long int i = begin_number; step > 0 ? i <= end_number : i >= end_number; i += step)
    sum += i;
    return sum;
}