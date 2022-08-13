<!--yml
category: codewars
date: 2022-08-13 11:48:07
-->

# 【Codewars】Build a pile of Cubes_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/89791922?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-89791922.nonecase](https://blog.csdn.net/ecysakura/article/details/89791922?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-89791922.nonecase)

### Codewars里的 6kyu Kata。

### 题目说明：

> Your task is to construct a building which will be a pile of n cubes. The cube at the bottom will have a volume of n^3, the cube above will have volume of (n-1)^3 and so on until the top which will have a volume of 1^3.
> 
> You are given the total volume m of the building. Being given m can you find the number n of cubes you will have to build?
> 
> The parameter of the function findNb `(find_nb, find-nb, findNb)` will be an integer m and you have to return the integer n such as n^3 + (n-1)^3 + ... + 1^3 = m if such a n exists or -1 if there is no such n.
> 
> ## Examples:
> 
> ```
> findNb(1071225) --> 45
> findNb(91716553919377) --> -1
> ```
> 
> ```
> mov rdi, 1071225
> call find_nb            ; rax <-- 45
> 
> mov rdi, 91716553919377
> call find_nb            ; rax <-- -1
> ```

题目的要求是给你一个数 (long) 让你判断它是否为一个立方和，如：

*   1 -> true -> return 1
*   8 -> false -> return -1
*   9 -> true -> return 2

这就需要使用到数学的知识，当然更简单的方法就是直接循环，直到 sum 值大于等于目标值 m 时，退出循环判断。依据结果返回答案。

### 解题代码：

```
public class ASum {
    public static long findNb(long m) {
        // your code
        //return (long)((Math.pow((1+8*Math.pow(m,0.5)),0.5)-1)/2) == ((Math.pow((1+8*Math.pow(m,0.5)),0.5)-1)/2) ? (long)((Math.pow((1+8*Math.pow(m,0.5)),0.5)-1)/2) : -1;
        long mm = 0;
        long n = 0;
        while(mm < m){
            n = n + 1;
            mm = mm + n * n * n;
        }
        if(mm == m){
            return n;
        }
        return -1;
    }  
}
```

### 个人总结：

题目不难，但是我想用一行代码解决，但是受限于精度的问题，不能通过所有的测试实例 (2147815493455852901L 与 2147815493455852900L 计算下来最后的结果是相等的)，但还有一种方式：我们可以先对 m 开方，这个时候 m 值就大大的减小了，可以减少计算的负担，也可以提高一些精度。