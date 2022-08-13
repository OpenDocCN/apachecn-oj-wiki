<!--yml
category: codewars
date: 2022-08-13 11:48:26
-->

# codewars_Integers: Recreation One_德华的神兜兜的博客-CSDN博客

> 来源：[https://blog.csdn.net/anbncn1234/article/details/104364809?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-104364809.nonecase](https://blog.csdn.net/anbncn1234/article/details/104364809?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-104364809.nonecase)

1, 我的代码
执行超时，欢迎大佬指教。

```
 def factor(num):
    sum = 0
    for i in range(1,num+1):
        if num % i == 0:
            sum += pow(i, 2)

    return sum

def checkifsquared(num):
    s = num**0.5
    s1 = str(s)

    if s1.endswith('.0'):
        return True
    else:
        return False

def list_squared(m, n):

    buffer = []
    for x in range(m,n+1):
        sum = factor(x)
        if checkifsquared(sum) == True:
            buffer.append([x, sum])

    return buffer 
```