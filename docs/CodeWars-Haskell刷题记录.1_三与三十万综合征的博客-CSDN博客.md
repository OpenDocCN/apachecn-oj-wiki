<!--yml
category: codewars
date: 2022-08-13 11:50:10
-->

# CodeWars-Haskell刷题记录.1_三与三十万综合征的博客-CSDN博客

> 来源：[https://blog.csdn.net/zeroven/article/details/108919726?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-108919726.nonecase](https://blog.csdn.net/zeroven/article/details/108919726?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-108919726.nonecase)

# 不定期更新一些Haskell刷题记录

[codewars主页](https://www.codewars.com/users/%E5%8F%81%E4%B8%8E%E5%8F%81%E6%8B%BE%E4%B8%87%E7%BB%BC%E5%90%88%E5%BE%81)

## Last digit of a large number

题目要求输入两个整数a, b, 输出 a^b 的最后一位数

题解:

```
lastDigit :: Integer -> Integer -> Integer
lastDigit _ 0 = 1
lastDigit a b = case mod a 10 of 
                0 -> 0
                1 -> 1
                2 -> [6,2,4,8] !! fromInteger (mod b 4)
                3 -> [1,3,9,7] !! fromInteger (mod b 4)
                4 -> if odd b then 4 else 6
                5 -> 5
                6 -> 6
                7 -> [1,7,9,3] !! fromInteger (mod b 4)
                8 -> [6,8,4,2] !! fromInteger (mod b 4)
                9 -> if odd b then 9 else 1 
```

Integer和Int要转换

这题的意思应该都能看懂吧不想赘述…最直接的解法了

当然每次刷hasekell的题目就是为了看别人的一行流解法:

```
lastDigit :: Integer -> Integer -> Integer
lastDigit a b = ((a `rem` 10) ^ ((b - 1) `rem` 4 + 1)) `rem` 10 
```

~~不会真的有人不知道rem是商吧， 不会吧不会吧~~

~~拿这题作为记录的第一题好像不太行~~

## Primes in numbers

原题:

```
Given a positive number n > 1 find the prime factor decomposition of n. The result will be a string with the following form :

 "(p1**n1)(p2**n2)...(pk**nk)"
where a ** b means a to the power of b

with the p(i) in increasing order and n(i) empty if n(i) is 1.

Example: n = 86240 should return "(2**5)(5)(7**2)(11)" 
```

题意就是因数分解然后格式化输出

题解:

```
import Data.List

prime_factors :: Integer -> String
prime_factors =
    concatMap
            (\x -> if length x == 1
                then "(" ++ show (head x) ++ ")"
                else "(" ++ show (head x) ++ "**" ++ show (length x) ++ ")"
            )
       . group
       . prime_factors' 2
       . fromInteger

prime_factors' :: Int -> Int -> [Int]
prime_factors' y x | y ^ 2 > x      = [x]
                   | x `mod` y == 0 = y : prime_factors' y (x `div` y)
                   | otherwise      = prime_factors' (y + 1) x 
```

1.  Integer类型转化为Int类型
2.  prime_factors’函数得到整数的因数列表
3.  group给列表中相同内容分组，刷题常用函数
4.  concatMap按照要求转化为格式化字符串
5.  **.** 挺好用的，柯里化