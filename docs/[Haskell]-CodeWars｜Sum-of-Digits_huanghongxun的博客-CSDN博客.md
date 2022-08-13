<!--yml
category: codewars
date: 2022-08-13 11:45:49
-->

# [Haskell] CodeWars|Sum of Digits_huanghongxun的博客-CSDN博客

> 来源：[https://blog.csdn.net/huanghongxun/article/details/78158709?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-78158709.nonecase](https://blog.csdn.net/huanghongxun/article/details/78158709?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-78158709.nonecase)

[https://www.codewars.com/kata/541c8630095125aba6000c00/haskell](https://www.codewars.com/kata/541c8630095125aba6000c00/haskell)

# 题目

本题你需要写一个Digital Root函数。
Digital root是一个数字所有位的递归和。给定n，算出n各位的和 n′ ，继续这个操作直到 n(p)=n(p−1) 。

以下是范例：

```
digital_root(16)
=> 1 + 6
=> 7

digital_root(942)
=> 9 + 4 + 2
=> 15 ...
=> 1 + 5
=> 6

digital_root(132189)
=> 1 + 3 + 2 + 1 + 8 + 9
=> 24 ...
=> 2 + 4
=> 6

digital_root(493193)
=> 4 + 9 + 3 + 1 + 9 + 3
=> 29 ...
=> 2 + 9
=> 11 ...
=> 1 + 1
=> 2
```

# 题解

1.  模拟法：

```
module DigitalRoot where

import Data.Char

digitalRoot :: Integral a => a -> a
digitalRoot x
    | x < 10 = x
    | otherwise = digitalRoot $ fromIntegral $ sum (map digitToInt $ show $ toInteger x)
```

1.  数学法

```
module DigitalRoot where

digitalRoot :: Integral a => a -> a
digitalRoot n = 1 + (n - 1) `rem` 9
```