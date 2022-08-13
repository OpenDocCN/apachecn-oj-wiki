<!--yml
category: codewars
date: 2022-08-13 11:48:39
-->

# Codewars解题Playing with digits_kaisens的博客-CSDN博客

> 来源：[https://blog.csdn.net/kaisens/article/details/78816810?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-78816810.nonecase](https://blog.csdn.net/kaisens/article/details/78816810?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-78816810.nonecase)

### 题目

> Some numbers have funny properties. For example:
> 
> 89 –> 8¹ + 9² = 89 * 1
> 
> 695 –> 6² + 9³ + 5⁴= 1390 = 695 * 2
> 
> 46288 –> 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 * 51 Given a
> positive integer n written as abcd… (a, b, c, d… being digits) and
> a positive integer p we want to find a positive integer k, if it
> exists, such as the sum of the digits of n taken to the successive
> powers of p is equal to k * n. In other words:
> 
> Is there an integer k such as : (a ^ p + b ^ (p+1) + c ^(p+2) + d ^
> (p+3) + …) = n * k If it is the case we will return k, if not return
> -1.
> 
> Note: n, p will always be given as strictly positive integers.
> 
> digPow(89, 1) should return 1 since 8¹ + 9² = 89 = 89 * 1 digPow(92,
> 1) should return -1 since there is no k such as 9¹ + 2² equals 92 * k
> digPow(695, 2) should return 2 since 6² + 9³ + 5⁴= 1390 = 695 * 2
> digPow(46288, 3) should return 51 since 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ =
> 2360688 = 46288 * 51

### 谷歌翻译:

> 给定一个正整数n写成abcd …（a，b，c，d
> …是数字）和一个正整数p，我们想要找到一个正整数k，如果存在的话，比如数字的总和对于p的连续幂的n等于k * n。换一种说法：
> 
> 是否有整数k，例如：（a ^ p + b ^（p + 1）+ c ^（p + 2）+ d ^（p + 3）+ …）= n * k
> 如果是这种情况，我们将返回k，如果不返回-1。
> 
> 注：n，p将始终作为严格正整数给出。

### 我的理解

参数:给一个正整数n=abcde; 与p
abcde带表各个位上的数字

如果a^p+b^(p+1)+c^(p+2)+d^(p+3)+e^(p+4)暂且把值写为sum
如果sum%n==0;就返回sum/0;
否则返回-1;

### 以下为我的代码

```
public class DigPow {

    public static long digPow(int n, int p) {

    long tem = -1;

    int sum = 0 ;

    int ss = n;

    int p1 = p+(n+"").length()-1;

    while(n!=0){

      int m = n%10;

      int m1 = m;
      for(int i = 0 ;i<p1-1;i++){

        m*=m1;
      }

      p1--;

      sum+=m;

      n = n/10;
    }

    if(sum%ss==0){

      tem=sum/ss;
    }
    return tem;
    }

}
```

该方法以通过测验

以下为评分最高的解决方案

```
public class DigPow {

  public static long digPow(int n, int p) {
    String intString = String.valueOf(n);
    long sum = 0;
    for (int i = 0; i < intString.length(); ++i, ++p)
      sum += Math.pow(Character.getNumericValue(intString.charAt(i)), p);
    return (sum % n == 0) ? sum / n : -1;
  }

}
```

很高兴可以看得懂
目前的水平在6k徘徊,有时连7k的题都解决不了