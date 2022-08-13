<!--yml
category: codewars
date: 2022-08-13 11:47:20
-->

# [codewars] | playing with digits_超帅的T T的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_43519498/article/details/86583703?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-86583703.nonecase](https://blog.csdn.net/qq_43519498/article/details/86583703?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-86583703.nonecase)

# playing with digits

下面来分享一题来自codewars的题目以及codewars上的优秀答案。

* * *

## instructions

Some numbers have funny properties. For example:

89 --> 8¹ + 9² = 89 * 1

695 --> 6² + 9³ + 5⁴= 1390 = 695 * 2

46288 --> 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 * 51
Given a positive integer n written as abcd… (a, b, c, d… being digits) and a positive integer p we want to find a positive integer k, if it exists, such as the sum of the digits of n taken to the successive powers of p is equal to k * n. In other words:

Is there an integer k such as : (a ^ p + b ^ (p+1) + c ^(p+2) + d ^ (p+3) + …) = n * k
If it is the case we will return k, if not return -1.

Note: n, p will always be given as strictly positive integers.

dig_pow(89, 1) should return 1 since 8¹ + 9² = 89 = 89 * 1
dig_pow(92, 1) should return -1 since there is no k such as 9¹ + 2² equals 92 * k
dig_pow(695, 2) should return 2 since 6² + 9³ + 5⁴= 1390 = 695 * 2
dig_pow(46288, 3) should return 51 since 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 * 51

## 以下是codewars上的一个优秀答案

```
int digPow(int n, int p) {
 //用这个函数求位数 
  int numDigits = floor(log10(n))+1;                      
  int result = 0;
  int num = n;
  for (int i = p + numDigits - 1; i >= p; i--) {
    result += pow(num%10, i);
    num/=10;
  }
  if (result % n == 0) {
    return result / n;
  }
  return -1;
} 
```