<!--yml
category: codewars
date: 2022-08-13 11:47:46
-->

# codewars - Sum of Intervals_德华的神兜兜的博客-CSDN博客

> 来源：[https://blog.csdn.net/anbncn1234/article/details/104652957?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-104652957.nonecase](https://blog.csdn.net/anbncn1234/article/details/104652957?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-104652957.nonecase)

codewars - Sum of Intervals

我的代码：

```
def sum_of_intervals(intervals):
    a = set()
    for r in intervals:

        for _ in range(r[0],r[1]):

            a.add(_)

    return len(a) 
```