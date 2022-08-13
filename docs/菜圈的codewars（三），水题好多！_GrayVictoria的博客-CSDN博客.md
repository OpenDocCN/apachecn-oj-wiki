<!--yml
category: codewars
date: 2022-08-13 11:44:42
-->

# 菜圈的codewars（三），水题好多！_GrayVictoria的博客-CSDN博客

> 来源：[https://blog.csdn.net/GrayVictoria/article/details/51281569?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-51281569.nonecase](https://blog.csdn.net/GrayVictoria/article/details/51281569?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-51281569.nonecase)

```
<span style="background-color: rgb(255, 255, 255); font-family: Arial, Helvetica, sans-serif;">昨天只是适应了一下，今天才发现，basic级别太多水题了！！！</span>
```

```
<span style="font-family: Arial, Helvetica, sans-serif; background-color: rgb(255, 255, 255);">而且是随机可选的水题……</span>
```

难度也就是我们学校的oj……第一页这种样子的……

熟能生巧嘛~~~

先水再说喽……

今天做的这道题，大意就是输入任意字符串，除了最后四位其他都变成#号

我的代码一定是最笨的啦~~

```
# return masked string
def maskify(cc):
    cclist=list(cc)
    i=len(cc)-5
    while i>=0:
      cclist[i]='#'
      i=i-1
    cc=''.join(cclist)
    return cc
```

来看大神的

```
def maskify(cc):
    return "#"*(len(cc)-4) + cc[-4:]
```

啧啧啧……cc[-4:]应该是切片，意思是倒数第四个到倒数第一个