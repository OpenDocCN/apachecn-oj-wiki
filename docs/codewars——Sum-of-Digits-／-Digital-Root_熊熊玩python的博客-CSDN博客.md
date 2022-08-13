<!--yml
category: codewars
date: 2022-08-13 11:42:59
-->

# codewars——Sum of Digits / Digital Root_熊熊玩python的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41552148/article/details/99235319?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-99235319.nonecase](https://blog.csdn.net/weixin_41552148/article/details/99235319?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-99235319.nonecase)

> In this kata, you must create a digital root function.A digital root is the recursive sum of all the digits in a number. Given n, take the sum of the digits of n. If that value has more than one digit, continue reducing in this way until a single-digit number is produced. This is only applicable to the natural numbers.Here’s how it works:digital_root(16)

=> 1 + 6
=> 7
digital_root(942)
=> 9 + 4 + 2
=> 15 …
=> 1 + 5
=> 6
digital_root(132189)
=> 1 + 3 + 2 + 1 + 8 + 9
=> 24 …
=> 2 + 4
=> 6
digital_root(493193)
=> 4 + 9 + 3 + 1 + 9 + 3
=> 29 …
=> 2 + 9
=> 11 …
=> 1 + 1
=> 2

# 思路

看文章的意思，就是说必须把数字分解到全部是个位数才可以
我的想法：按数字提取每个位数的数字虽然我也能做到，但是毕竟还是太复杂，不如转化成字符串，进行字符串操作。
当然，最后还得用递归，递归结束的标志就是分解后的数字求和变成个位数。

```
 def digital(n):
    string = str(n)
    sum = 0
    for i in string:
        sum += int(i)
    if sum >= 10:
        return digital(sum)
    else:
        return sum 
```

# 总结

随着一年以来的学习，我发现自己的编程水平确实是看得见在提高的，当时很讨厌递归，但是做这个题的时候，第一反应就是递归。为自己加油！