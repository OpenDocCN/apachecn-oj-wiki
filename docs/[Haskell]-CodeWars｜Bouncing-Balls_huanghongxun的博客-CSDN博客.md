<!--yml
category: codewars
date: 2022-08-13 11:48:24
-->

# [Haskell] CodeWars|Bouncing Balls_huanghongxun的博客-CSDN博客

> 来源：[https://blog.csdn.net/huanghongxun/article/details/78159018?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-78159018.nonecase](https://blog.csdn.net/huanghongxun/article/details/78159018?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-78159018.nonecase)

[https://www.codewars.com/kata/5544c7a5cb454edb3c000047/haskell](https://www.codewars.com/kata/5544c7a5cb454edb3c000047/haskell)

# 题目

一个小孩在一个超高建筑的n楼打球，高度为 h(h>0) ，他把球丢出了建筑，垂直下落并弹起，每次弹起的高度是上一次的 bounce(0<bounce<1) 倍。他母亲从 window(window<h) 高度往窗外看。他母亲会看到多少次球呢？（看到球定义为球经过window的高度）
如果上述3个参数的条件都满足了，输出一个正整数表示他母亲会看到的球的次数，否则返回-1表示参数错误。

# 样例

```
h = 3, bounce = 0.66, window = 1.5, result is 3

h = 3, bounce = 1, window = 1.5, result is -1 (bounce >= 1).
```

# 题解

1.  模拟法

```
module Codewars.Kata.BouncingBall where

bouncingBall :: Double -> Double -> Double -> Integer
bouncingBall' h bounce window
    | h < window = 0
    | h == window = 1
    | otherwise = 2 + bouncingBall' (h * bounce) bounce window

bouncingBall h bounce window
    | bounce >= 1 || bounce <= 0 || h <= 0 || window >= h = -1
    | otherwise = 1 + bouncingBall' (h * bounce) bounce window
```

1.  数学法
    相当于求最大的n，使得
     h×(bounce)n>window

     n<logbouncewindowh

    那么有
     n=⌊logbouncewindowh⌋

    n表示弹跳的次数，显然母亲看到的次数就是 2n+1 了。

```
bouncingBall h b w
  | not (h > 0 && 0 < b && b < 1 && w < h) = -1
  | otherwise = floor (logBase b $ w / h) * 2 + 1
```