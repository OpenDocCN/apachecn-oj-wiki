<!--yml
category: codewars
date: 2022-08-13 11:49:40
-->

# CodeWars 给定数值的阶乘结果中包含多少0_happymff的博客-CSDN博客

> 来源：[https://blog.csdn.net/happymff/article/details/70809292?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-70809292.nonecase](https://blog.csdn.net/happymff/article/details/70809292?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-70809292.nonecase)

Description:

Write a program that will calculate the number of trailing zeros in a factorial of a given number.

[http://mathworld.wolfram.com/Factorial.html](http://mathworld.wolfram.com/Factorial.html)

N! = 1 * 2 * 3 * 4 … N

zeros(12) = 2 # 1 * 2 * 3 .. 12 = 479001600
that has 2 trailing zeros 4790016(00)
Be careful 1000! has length of 2568 digital numbers.

不需要求出阶乘结果，首先阶乘的值太大了，而我们只需要求出能够得到0的两个数的乘积就好了：

```
public class Solution {
  public static int zeros(int n) {
    int res = 0;
    for (int i = 5; i <= n; i *= 5) {
      res += n / i;
    }
    return res;
  }
}
```

My solution:

```
/**
 * Created by mff on 2017/4/26.
 */
public class Solution {
    public static int zeros(int n) {

        int count2 = 0;

        int count5 = 0;

        for (int number = 1; number <= n; number ++) {
            int dynmicNumber = number;
            while (dynmicNumber % 2 == 0) { 
                count2++;
                dynmicNumber /= 2;
            }
            while (dynmicNumber % 5 == 0) { 
                count5++;
                dynmicNumber /= 5;
            }
        }

        System.out.println("结尾0的个数为：" + Math.min(count2, count5));
        return  Math.min(count2, count5);
    }

} 
```