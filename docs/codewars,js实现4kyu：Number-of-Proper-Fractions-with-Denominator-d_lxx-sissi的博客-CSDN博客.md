<!--yml
category: codewars
date: 2022-08-13 11:51:53
-->

# codewars,js实现4kyu:Number of Proper Fractions with Denominator d_lxx-sissi的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_35438535/article/details/106260730?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-106260730.nonecase](https://blog.csdn.net/sinat_35438535/article/details/106260730?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-106260730.nonecase)

# 题目描述

该kata的链接地址: [link](https://www.codewars.com/kata/55b7bb74a0256d4467000070/train/javascript).

If n is the numerator and d the denominator of a fraction, that fraction is defined a (reduced) proper fraction if and only if GCD(n,d)==1.

For example 5/16 is a proper fraction, while 6/16 is not, as both 6 and 16 are divisible by 2, thus the fraction can be reduced to 3/8.

Now, if you consider a given number d, how many proper fractions can be built using d as a denominator?

For example, let’s assume that d is 15: you can build a total of 8 different proper fractions between 0 and 1 with it: 1/15, 2/15, 4/15, 7/15, 8/15, 11/15, 13/15 and 14/15.

You are to build a function that computes how many proper fractions you can build with a given denominator:

properFractions(1)==0
properFractions(2)==1
properFractions(5)==4
properFractions(15)==8
properFractions(25)==20
Be ready to handle big numbers.

Edit: to be extra precise, the term should be “reduced” fractions, thanks to girianshiido for pointing this out and sorry for the use of an improper word 😃

# Example

```
properFractions(1)==0
properFractions(2)==1
properFractions(5)==4
properFractions(15)==8
properFractions(25)==20 
```

# 代码实现

## 我第一次完成的代码（由于代码时间复杂度太高，编译超时了，未通过）

```
 function properFractions(n){

					  var sum = 0;   
					  for(var i = 2;i < n;i++){ 
					  	var flag = true;
					  	for (var j = 2;j <= i/2;j++) { 
					  		(i % j == 0) && (n % j == 0 && (flag = false)) 
					  	}
					  	n % i == 0 && (flag = false); 
					  	flag == true && sum++; 
					  }
					  return sum += 1 
				} 
```

## 欧拉函数（有点理不清，需要多研究扩展一下）

百度了一下发现这是欧拉函数

### 按照欧拉函数的公式完成的代码

```
 function properFractions(n){

    if (n === 1) return 0;
    let result = n, a = n;
    for (let i = 2; i <= Math.sqrt(a); i++) {
       if (a%i===0) {
            result = result/i*(i-1);
            while(a%i === 0) a /= i;
       }
    }
    if (a>1) result = result/a*(a-1)
    return result
  } 
```

资料参考：

[https://blog.csdn.net/update7/article/details/70943545](https://blog.csdn.net/update7/article/details/70943545)
[https://blog.csdn.net/weixin_43237242/article/details/97388834](https://blog.csdn.net/weixin_43237242/article/details/97388834)

# 思路

**我自己蛮力写的代码就是：**

1.  由于分子i是从1~n，1肯定和n是互质的，所以分子i从2开始循环到n；
2.  设置一个判断值flag，初始值为true；
3.  然后循环检测分子i和分母n是否能同时被小于等于i/2的数除断，只要存在，flag就等于false，当分母n能被i除断时，flag也等于false；
4.  只有当flag一直为true时，才进行计算

# 难点

我觉得难点就是这个欧拉函数了，不知道的话很难通过