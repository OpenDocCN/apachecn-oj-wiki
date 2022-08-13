<!--yml
category: codewars
date: 2022-08-13 11:44:20
-->

# 关于codewars.com一个问题，Growth of a Population的python解法_日尼禾尔月半的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_46091266/article/details/116573096?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-116573096.nonecase](https://blog.csdn.net/qq_46091266/article/details/116573096?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-116573096.nonecase)

# 关于codewars.com一个问题，Growth of a Population的python解法

Description:

In a small town the population is `p0 = 1000` at the beginning of a year. The population regularly increases by `2 percent` per year and moreover `50` new inhabitants per year come to live in the town. How many years does the town need to see its population greater or equal to `p = 1200` inhabitants?

如果按最高赞的或者网上的答案抄，会得到一个错误，就是结果是3而答案是4的错误，原因在下面：

```
At the end of the first year there will be: 
1000 + 1000 * 0.02 + 50 => 1070 inhabitants

At the end of the 2nd year there will be: 
1070 + 1070 * 0.02 + 50 => 1141 inhabitants (** number of inhabitants is an integer **)

At the end of the 3rd year there will be:
1141 + 1141 * 0.02 + 50 => 1213

It will need 3 entire years. 
```

More generally given parameters:

`p0, percent, aug (inhabitants coming or leaving each year), p (population to surpass)`

the function `nb_year` should return `n` number of entire years needed to get a population greater or equal to `p`.

aug is an integer, percent a positive or null floating number, p0 and p are positive integers (> 0)

```
import math

def nb_year(p0, percent, aug, p):
    # your code
    count = 0
    while p0 < p:
        p0 = p0 + math.floor(p0 * (percent / 100)) + aug
        count +=1
    return count
```

更简单点的：

```
import math

def nb_year(p0, percent, aug, p):
    count = 0
    while p0 < p:
        p0 += p0 * percent // 100 + aug
        count += 1
    return count

print(nb_year(1000, 2, 50, 1214))
```

或者Int(p0)它也行。

人这种生物，不能有小数点啊，0.5个人算人口吗？

所以最后没办法，只好面向答案编程，取地板数，后面小数的全部不算人。