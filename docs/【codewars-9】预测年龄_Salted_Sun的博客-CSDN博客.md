<!--yml
category: codewars
date: 2022-08-13 11:41:19
-->

# 【codewars-9】预测年龄_Salted_Sun的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42338512/article/details/123736332?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-9-123736332-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_42338512/article/details/123736332?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-9-123736332-null-null.142^v40^control,185^v2^control&utm_term=codewars)

My grandfather always predicted how old people would get, and right before he passed away he revealed his secret!

In honor of my grandfather’s memory we will write a function using his formula!

*   Take a list of ages when each of your great-grandparent died.
*   Multiply each number by itself.
*   Add them all together.
*   Take the square root of the result.
*   Divide by two.

```
Example
predictAge(65, 60, 75, 55, 60, 63, 64, 45) === 86 
```

Note: the result should be rounded down to the nearest integer.

**分析**
此题目难点不在求解的思路上. 而是面对多个参数时如何利用语言本身的语法特性来简化代码.

```
 #include <math.h>
int predictAge(int age1, int age2, int age3, int age4, int age5, int age6, int age7, int age8)
{
  return sqrt(age1*age1+age2*age2+age3*age3+age4*age4+age5*age5+age6*age6+age7*age7+age8*age8)/2;
} 
```

**更好的解法**

重点:

*   用`std::array<类型, 个数>` 来替代C数组, 以此获取使用模板的能力
*   typename后加省略号
*   类型名后加省略号
*   `sizeof...()`
*   对后续无须改变的变量一律用`const`修饰
*   `std::common_type_t<T...>` 返回公共最小父类型
*   `std::accumulate` 对数组中的值进行累加

```
#include <numeric> 
#include <cmath> 
#include <array> 

template <typename ... T>
int predictAge(const T ...ages)
{
  const std::array<std::common_type_t<T...>, sizeof...(T)> all_ages = { (ages*ages)... };

  const int sum = { std::accumulate(all_ages.begin(), all_ages.end(), 0) }; 

  const auto squared = std::sqrt(sum) / 2;

  return squared;
} 
```