<!--yml
category: codewars
date: 2022-08-13 11:27:02
-->

# CodeWars(1)--C语言_Edenist丶的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36624415/article/details/85058375?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-85058375.142^v40^control,185^v2^control](https://blog.csdn.net/qq_36624415/article/details/85058375?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-85058375.142^v40^control,185^v2^control)

从今往后我会不定期的写一些关于Codewars上面关于C语言的一些题目，个人认为这些题目用来练手真是再好不过了，但是没有leetcode上的题难，一步一步来嘛，上面的有些题目也很精彩很考验基本功。

我首先贴出问题，然后贴出自己的代码，再在我代码下面贴出我认为最厉害的解法（啪啪打脸）。当然，高手轻喷，能学到东西就好！

那么来看第一道吧！
问题描述：

**Some numbers have funny properties. For example:
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
dig_pow(46288, 3) should return 51 since 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 * 51**

emmm，英语不好的同学还是多学学英语吧，本人目前在国外，觉得英语好真的非常吃香！大家加油！

我的代码（实现说明一下，这里只写用来返回答案的函数，如果大家想测试，可以自己写一个主函数，直接输入测试数据，调用函数测试即可！）
以下自己写的代码没有进行优化，因为我自己会规定时间，大家尽量看吧，主要看看避免不要犯我的错误（-___-!)

```
int digPow(int n, int p) {
  int k;                     //number to return
  int i;
  double sum = 0.00;
  int numberOfdigit = 0;
  int flag = n;
  while(flag!=0)
  {
     flag/=10;
     numberOfdigit++;
  }
  for(i=0;i<numberOfdigit;i++)
  {
     double divide = pow(10,numberOfdigit-i-1);
     int finalDivide = (int)divide;
     //int ooo1= (int)pow(10,numberOfdigit-i-1);         //输出为99，损失了精度，但是如果分开写然后再强转，不会有问题出现
     sum+=pow(n/finalDivide%10, p+i);
  }
  if(((int)(sum))%n==0)
  {
     k=sum/n;
     return k;
  }else
  {
     return -1;
  }
} 
```

接下来是大神的答案，大家一定要看懂！这个票数真的非常高！能得到不少的提高！

```
int digPow(int n, int p) {
  int numDigits = floor(log10(n))+1;                       //学到了 用这个函数求位数 谁能有我笨？
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

第一道题结束了，大家自己练练吧！