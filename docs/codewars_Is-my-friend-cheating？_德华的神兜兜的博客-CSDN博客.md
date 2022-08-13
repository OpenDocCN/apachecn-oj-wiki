<!--yml
category: codewars
date: 2022-08-13 11:50:22
-->

# codewars_Is my friend cheating?_德华的神兜兜的博客-CSDN博客

> 来源：[https://blog.csdn.net/anbncn1234/article/details/104331590?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-104331590.nonecase](https://blog.csdn.net/anbncn1234/article/details/104331590?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-104331590.nonecase)

Codewars 里的Is my friend cheating?

执行超时， 求大佬指教

```
def removNb(n):

    buffer = []
    sum = 0
    for x in range(0,n+1):
        sum += x
    print(sum)
    for i in range(1,n+1):
        for j in range(1,n+1):
            if i !=j and i*j == sum - i - j:
                buffer.append([i, j])

    print(buffer)
    return buffer 
```