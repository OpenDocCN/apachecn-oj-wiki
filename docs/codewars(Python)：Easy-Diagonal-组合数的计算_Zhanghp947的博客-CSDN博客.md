<!--yml
category: codewars
date: 2022-08-13 11:49:19
-->

# codewars(Python):Easy Diagonal 组合数的计算_Zhanghp947的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_44389971/article/details/104581828?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-104581828.nonecase](https://blog.csdn.net/weixin_44389971/article/details/104581828?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-104581828.nonecase)

# codewars(Python):Easy Diagonal

## Instructions

In the drawing below we have a part of the Pascal’s triangle, lines are numbered from zero (top). The left diagonal in pale blue with only numbers equal to 1 is diagonal zero, then in dark green (1, 2, 3, 4, 5, 6, 7) is diagonal 1, then in pale green (1, 3, 6, 10, 15, 21) is diagonal 2 and so on.解释一下原题并没有给出图片，不过上题所指的就是杨辉三角。
[杨辉三角](https://baike.baidu.com/item/%E6%9D%A8%E8%BE%89%E4%B8%89%E8%A7%92/215098?fromtitle=Pascal%27s%20Triangle&fromid=18082658&fr=aladdin)
We want to calculate the sum of the binomial coefficients on a given diagonal. The sum on diagonal 0 is 8 (we’ll write it S(7, 0), 7 is the number of the line where we start, 0 is the number of the diagonal). In the same way S(7, 1) is 28, S(7, 2) is 56.Can you write a program which calculate S(n, p) where n is the line where we start and p is the number of the diagonal?The function will take n and p (with: n >= p >= 0) as parameters and will return the sum.

## Examples:

diagonal(20, 3) => 5985
diagonal(20, 4) => 20349

## Hint:

When following a diagonal from top to bottom have a look at the numbers on the diagonal at its right.

## 我的代码

这道题目呢难的不是理解题目，是算法，我试了，不是递归深度超了，而且不知道为什么设置了，也没有办法通过测试。难在算组合数。最后直接找了scipy库，对于最后的答案要用到C(n,m)=C(n-1,m-1)+C(n-1,m)这个性质合并一下。
对scipy库介绍一下吧，是一个第三方的科学计算包，要自己安装的。用这个包可以直接算出组合数。

```
from scipy.misc import comb
def diagonal(n, p):
    return comb(n+1, p+1, exact=True)
```