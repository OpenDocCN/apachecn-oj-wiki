<!--yml
category: codewars
date: 2022-08-13 11:46:16
-->

# [Codewars]-Number of Proper Fractions with Denominator d___Charming__的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41882147/article/details/80998615?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-80998615.nonecase](https://blog.csdn.net/qq_41882147/article/details/80998615?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-80998615.nonecase)

### 具有分母d的适当分数的数量(Number of Proper Fractions with Denominator d)

### 题目：

*   简单说就是以n为分母的，不能化简的，真分数，有多少个。
*   以`n=16`举个例子：

    *   `5/16`是符合题意的，而`6/16`可以化简为`3/8`故不合题意，不计算在内。
    *   一共有8个符合题意的真分数：`1/15, 2/15, 4/15, 7/15, 8/15, 11/15, 13/15 和 14/15`
*   测试用例

```
properFractions(1)==0
properFractions(2)==1
properFractions(5)==4
properFractions(15)==8
properFractions(25)==20
```

### 思路：

*   一开始的时候我是直接暴力破解的，发现时间复杂度很高（ N∗N−−√ N ∗ N ）
*   后来对寻找质因数做了很多优化，还是不行，时间爆栈了。
*   接着问了下度娘发现这其实是一个很经典的问题：**寻找1到N中与N互质的数**，也就是**欧拉函数**了
*   接着用代码实现欧拉函数就好了
*   文末有几个参考文档可以阅读一下

### 解答：

```
function properFractions(n){

    if (n === 1) return 0;
    let res = n, a = n;
    for (let i = 2; i <= Math.sqrt(a); i++) {
       if (a%i===0) {
            res = res/i*(i-1);
            while(a%i === 0) a /= i;
       }
    }
    if (a>1) res = res/a*(a-1)
    return res
}
```

### 参考文档

1.[欧拉函数的求法与应用——sentimental_dog](https://blog.csdn.net/sentimental_dog/article/details/52002608)
2.[欧拉函数——Lur](https://blog.csdn.net/once_hnu/article/details/6302868)