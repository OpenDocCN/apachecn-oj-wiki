<!--yml
category: codewars
date: 2022-08-13 11:47:33
-->

# [Haskell] CodeWars|Build a pile of Cubes_huanghongxun的博客-CSDN博客

> 来源：[https://blog.csdn.net/huanghongxun/article/details/78158374?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-78158374.nonecase](https://blog.csdn.net/huanghongxun/article/details/78158374?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-78158374.nonecase)

[https://www.codewars.com/kata/5592e3bd57b64d00f3000047/haskell](https://www.codewars.com/kata/5592e3bd57b64d00f3000047/haskell)

# 题目

你的任务是构建一个建筑物，这个建筑物由n个立方体构成，最底层的立方体体积为 n3 ，直到最高层的立方体体积为 13 。

给定整个建筑物的总体积m，你知道这个建筑物有多少个立方体吗？

如果没有n能对应m，输出-1。

# 样例

```
findNb 1071225 = 45
findNb 91716553919377 = -1
```

# 题解

因为

13+23+⋯+n3=(1+2+⋯+n)2=(n(n+1)2)2

所以。。

```
module Codewars.Kata.PileOfCubes where

findNb :: Integer -> Integer

findNb m
    | div (root * (root + 1)) 2 ^ 2 == m = root
    | otherwise = -1
    where
        intSqrt = floor . sqrt . fromIntegral
        root = intSqrt (intSqrt m * 2)
```