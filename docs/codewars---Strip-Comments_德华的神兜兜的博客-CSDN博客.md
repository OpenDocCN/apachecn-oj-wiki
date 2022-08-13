<!--yml
category: codewars
date: 2022-08-13 11:45:44
-->

# codewars - Strip Comments_德华的神兜兜的博客-CSDN博客

> 来源：[https://blog.csdn.net/anbncn1234/article/details/104780741?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-104780741.nonecase](https://blog.csdn.net/anbncn1234/article/details/104780741?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-104780741.nonecase)

```
def solution(string,markers):
    l = string.split("\n")
    for i in range(len(l)):
        for j in markers:
            if j in l[i]:
                index1 = l[i].index(j)
                l[i] = l[i][0:index1]

    for x in range(len(l)):
        l[x] = l[x].rstrip(" ")

    res = "\n".join(l)
    return res 
```