<!--yml
category: codewars
date: 2022-08-13 11:41:56
-->

# Codewars刷题升级 （Python）7Kyu Find the divisors! 找除数_Howar Yick的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41432655/article/details/90416397?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-28-90416397-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_41432655/article/details/90416397?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-28-90416397-null-null.142^v40^control,185^v2^control&utm_term=codewars)

**题目描述：**

> Create a function named divisors/Divisors that takes an integer n > 1 and returns an array with all of the integer’s divisors(except for 1 and the number itself), from smallest to largest. If the number is prime return the string ‘(integer) is prime’.
> 建立一个函数divisors/Divisors，参数为整数且大于1，返回一个数组，数组由参数的除数从小到大组成（不包括1和参数本身)，如果参数是一个素数，返回字符串’(integer)
> is prime’。

**举例：**

> divisors(12); #should return [2,3,4,6]
> divisors(25); #should return[5]
> divisors(13); #should return “13 is prime”

**解题思路：**
建立一个数组，从2起循环，如果余数为0则append()到数组列表。最后判断数组是否大于0，大于返回数组，等于0则为素数。

**代码实现：**

```
def divisors(integer):
    result = []
    for i in range(2, integer):
        if integer % i == 0:
            result.append(i)
    if len(result) > 0:
        return result
    else:
        return str(integer) + " is prime" 
```