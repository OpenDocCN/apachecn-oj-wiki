<!--yml
category: codewars
date: 2022-08-13 11:48:06
-->

# codewars(Python):Next polydivisible number_Zhanghp947的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_44389971/article/details/104539491?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-104539491.nonecase](https://blog.csdn.net/weixin_44389971/article/details/104539491?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-104539491.nonecase)

# codewars(Python):Next polydivisible number

## Instructions

Given a non-negative number, return the next bigger polydivisible number, or an empty value like null or Nothing.
A number is polydivisible if its first digit is cleanly divisible by 1, its first two digits by 2, its first three by 3, and so on. There are finitely many polydivisible numbers.
这里解释一下累进可除数polydivisible number:首个位非零，而且由它首n个位组成的数是n的倍数。
举个例子，像123252，取前一个数字即1可整除1，取前二个数字即12可整除2，取前三个数字123可整除3，以此类推，取前六个数字也可以整除6

## sample example

next_num(0)>>1
next_num(10)>>12
next_num(11)>>12
next_num(1234)>>1236
next_num(123220)>>123252

## 我的代码

代码注释得很详细了，就不再解释解法了

```
def next_num(n):
    n+=1
    while n<=3608528850368400786036725:
        pr=ifpol(n) 
        if pr==True:
            return n
        else:
            s=len(str(n))
            num=10**(s-pr) 
            n=(n//num+1)*num
def ifpol(n):
    s=len(str(n))
    for i in range(1,s+1):
        if n//(10**(s-i))%i!=0:
            return i
    return True 
```