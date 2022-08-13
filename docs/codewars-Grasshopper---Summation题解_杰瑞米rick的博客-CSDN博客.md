<!--yml
category: codewars
date: 2022-08-13 11:45:15
-->

# codewars Grasshopper - Summation题解_杰瑞米rick的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42561106/article/details/84930883?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-84930883.nonecase](https://blog.csdn.net/weixin_42561106/article/details/84930883?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-84930883.nonecase)

Summation
Write a program that finds the summation of every number from 1 to num. The number will always be a positive integer greater than 0.

For example:

summation(2) -> 3
1 + 2

summation(8) -> 36
1 + 2 + 3 + 4 + 5 + 6 + 7 + 8

思路：1.数学思维，联想到这是求公差为1的前num项和，可以直接引用等差数列前n 项和
公式，sum=n*(n-1)/2.
2.循环，运用循环结构求和。
`

```
int summation(int num){
  int sum=0;
  for(int i=0;i<=num;i++)
    {
      sum=sum+i;
    }
    return sum;
} 
```

在这里插入代码片

```
int summation(int num){
 return num*(num-1)/2;
} 
```