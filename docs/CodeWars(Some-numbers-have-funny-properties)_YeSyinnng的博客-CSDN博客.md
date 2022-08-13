<!--yml
category: codewars
date: 2022-08-13 11:48:42
-->

# CodeWars(Some numbers have funny properties)_YeSyinnng的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_39532595/article/details/85805154?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-85805154.nonecase](https://blog.csdn.net/qq_39532595/article/details/85805154?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-85805154.nonecase)

老规矩，上题目：

> Some numbers have funny properties. For example:
> 89 --> 8¹ + 9² = 89 * 1
> 695 --> 6² + 9³ + 5⁴= 1390 = 695(n) * 2(k)=sum //最后的结果 = n*k k = 最后的结果
> 46288 --> 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 * 51
> Given a positive integer n written as abcd… (a, b, c, d… being digits) and a positive integer p we want to find a positive integer k, if it exists, such as the sum of the digits of n taken to the successive powers of p is equal to k * n. In other words:
> Is there an integer k such as : (a ^ p + b ^ (p+1) + c ^(p+2) + d ^ (p+3) + …) = n * k
> If it is the case we will return k, if not return -1.
> Note: n, p will always be given as strictly positive integers.

解析题目：
1.给两个参数，第一个参数进行分解，第二个参数是初始的次幂，根据第一个参数的个数进行次幂的增加
2.返回值是，参数分解后次幂的累加 除以第一个参数 余数为零的时候 返回两者的商，不存在的时候返回-1

代码：

```
 function digPow(n,p){
        var sum=0;
        var res =String(n).split('');   //分割成数组
        for(var i=0;i<res.length;i++){
          sum +=Math.pow(res[i],p++);
        }
           if(sum%n===0){        
               return sum/n;      //返回商
           }else{
               return -1;
           }
    }
    console.log(digPow(46288, 3));
    console.log(digPow(92, 1)); 
```

今天在写的时候，断网了，刷新了一下题目就换了，然后就只能放自己代码啦，哪天碰见了，再把大佬的放上来~嗯，再写一题：）