<!--yml
category: codewars
date: 2022-08-13 11:51:30
-->

# codewars,js实现5kyu:ntegers: Recreation One_lxx-sissi的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_35438535/article/details/106243843?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-106243843.nonecase](https://blog.csdn.net/sinat_35438535/article/details/106243843?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-106243843.nonecase)

# 题目描述

该kata的链接地址: [link](https://www.codewars.com/kata/55aa075506463dac6600010d/train/javascript/5ec4f722d7cf620028cfe5bc).

Divisors of 42 are : 1, 2, 3, 6, 7, 14, 21, 42\. These divisors squared are: 1, 4, 9, 36, 49, 196, 441, 1764\. The sum of the squared divisors is 2500 which is 50 * 50, a square!

Given two integers m, n (1 <= m <= n) we want to find all integers between m and n whose sum of squared divisors is itself a square. 42 is such a number.

The result will be an array of arrays or of tuples (in C an array of Pair) or a string, each subarray having two elements, first the number whose squared divisors is a square and then the sum of the squared divisors.

#Examples:

list_squared(1, 250) --> [[1, 1], [42, 2500], [246, 84100]]
list_squared(42, 250) --> [[42, 2500], [246, 84100]]
The form of the examples may change according to the language, see Example Tests: for more details.

Note

In Fortran - as in any other language - the returned string is not permitted to contain any redundant trailing whitespace: you can use dynamically allocated character strings.

# Example

```
Test.describe("Basic tests",function() {
Test.assertSimilar(listSquared(1, 250), [[1, 1], [42, 2500], [246, 84100]])
Test.assertSimilar(listSquared(42, 250), [[42, 2500], [246, 84100]])
Test.assertSimilar(listSquared(250, 500), [[287, 84100]])
}) 
```

# 我完成代码

```
 function listSquared(m, n) {

				    var result = [];
				    for(var i = m;i <= n;i++){
				    	var sum = 0;
				    	for (var j = 1;j <= i/2;j++) {
				    		i % j == 0 && (sum += j*j);
				    	}
				    	Math.sqrt(sum+i*i)%1 == 0 && result.push([i,sum+i*i]);
				    }
				    return result;
				} 
```

# 我的思路

**题目要实现找出m到n之间的一些数字，这些数字的除数的平方和恰好开方为整数**

1.循环出m到n之间的数i，每次循环开始的时候都需要重置sum为0；

2.然后在循环出1到i/2（大于i/2的话是肯定不能被除断的）之间的数,找出i的除数平方之后加起来，得出总和sum;

3.由于i是肯定可以被其本身整除的，所以sum开方的时候要加上i*i,如果开方出来的是整数的话，就把i和总和存起来，

# 难点

水平有限，可能我写的这个代码时间复杂度会比较高