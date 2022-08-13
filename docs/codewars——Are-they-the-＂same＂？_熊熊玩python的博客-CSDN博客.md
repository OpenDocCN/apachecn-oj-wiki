<!--yml
category: codewars
date: 2022-08-13 11:40:22
-->

# codewars——Are they the "same"?_熊熊玩python的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41552148/article/details/98762166?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-16-98762166-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_41552148/article/details/98762166?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-16-98762166-null-null.142^v40^control,185^v2^control&utm_term=codewars)

> Given two arrays a and b write a function comp(a, b) (compSame(a, b) in Clojure) that checks whether the two arrays have the “same” elements, with the same multiplicities. “Same” means, here, that the elements in b are the elements in asquared, regardless of the order.ExamplesValid arraysa = [121, 144, 19, 161, 19, 144, 19, 11]

> b = [121, 14641, 20736, 361, 25921, 361, 20736, 361]comp(a, b) returns true because in b 121 is the square of 11, 14641 is the square of 121, 20736 the square of 144, 361 the square of 19, 25921 the square of 161, and so on. It gets obvious if we write b’s elements in terms of squares:a = [121, 144, 19, 161, 19, 144, 19, 11]
> b = [11*11, 121*121, 144*144, 19*19, 161*161, 19*19, 144*144, 19*19]Invalid arraysIf we change the first number to something else, comp may not return true anymore:a = [121, 144, 19, 161, 19, 144, 19, 11]
> b = [132, 14641, 20736, 361, 25921, 361, 20736, 361]comp(a,b) returns false because in b 132 is not the square of any number of a.a = [121, 144, 19, 161, 19, 144, 19, 11]
> b = [121, 14641, 20736, 36100, 25921, 361, 20736, 361]comp(a,b) returns false because in b 36100 is not the square of any number of a.Remarksa or b might be [] (all languages except R, Shell). a or b might be nil or nullor None or nothing (except in Haskell, Elixir, C++, Rust, R, Shell, PureScript).If a or b are nil (or null or None), the problem doesn’t make sense so return false.If a or b are empty then the result is self-evident.a or b are empty or not empty lists.

# 思路

## 惭愧，我的思路很糟糕，各种for循环遍历，做完之后看了大神的操作，惊为天人

# 总结

## 尝试去运用一些py的语法糖，对于try的捕获异常也要更加深刻的理解，我自己本来的代码，甚至还加入了判定列表是否为空，是否为空列表，增加程序的运算量。

```
def comp(array1, array2): 
    try: 
        return sorted([i ** 2 for i in array1]) == sorted(array2)     
    except: 
        return False 
```