<!--yml
category: codewars
date: 2022-08-13 11:44:57
-->

# 【Codewars-snail】顺时针打印矩阵（python）_喝咖啡的熊的博客-CSDN博客

> 来源：[https://blog.csdn.net/crowhe1993/article/details/52842095?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-52842095.nonecase](https://blog.csdn.net/crowhe1993/article/details/52842095?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-52842095.nonecase)

【题目】
给定一个矩阵，顺时针打印该矩阵
【解法】

递归版本

def snail(array):
return list(array[0]) + snail(zip(*array[1:])[::-1]) if array else []

非递归版本

```
def snail(array):
    a = []
    while array:
        a.extend(list(array.pop(0)))
        array = zip(*array)
        array.reverse()
    return a
```

最近发现自己对于zip函数的用法还是掌握的不好，在这里也记录一下zip函数吧。目前还是只是出于知道这个函数表示的是什么意思，但是不能在需要用的时候想起来。

这个链接对zip函数的用法讲解感觉比较详细：
[http://www.cnblogs.com/BeginMan/archive/2013/03/14/2959447.html](http://www.cnblogs.com/BeginMan/archive/2013/03/14/2959447.html)

感觉zip在进行矩阵转置的时候用的很多，这里也就顺便贴一下矩阵转置的代码。
【题目】
矩阵转置
【解法】

```
def Matrix_zhuan(array):
    return map(list,zip(*array))
```

这里还有map函数，也借此复习一下map函数的用法。map(function,sequence)其中，function是函数功能，可以是自己定义的也可以是系统自带的，sequence是一个可迭代的对象，如列表。