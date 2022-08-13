<!--yml
category: codewars
date: 2022-08-13 11:49:18
-->

# codewars - Human Readable Time_德华的神兜兜的博客-CSDN博客

> 来源：[https://blog.csdn.net/anbncn1234/article/details/104511653?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-104511653.nonecase](https://blog.csdn.net/anbncn1234/article/details/104511653?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-104511653.nonecase)

codewars - Human Readable Time

1.  我的代码

```
def make_readable(seconds):

    hh = 0
    mm = 0
    ss = seconds
    while ss >= 60:
        ss -= 60
        mm += 1
        if mm == 60:
            mm = 0
            hh += 1
    print(hh,mm,ss)
    print('%02d:%02d:%02d'% (hh,mm,ss))
    return '%02d:%02d:%02d'% (hh,mm,ss) 
```