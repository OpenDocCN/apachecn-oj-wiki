<!--yml
category: codewars
date: 2022-08-13 11:51:15
-->

# [Codewars]-Pyramid Slide Down_德华的神兜兜的博客-CSDN博客

> 来源：[https://blog.csdn.net/anbncn1234/article/details/104655591?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-104655591.nonecase](https://blog.csdn.net/anbncn1234/article/details/104655591?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-104655591.nonecase)

[Codewars]-Pyramid Slide Down

代码：

```
def longest_slide_down(pyramid):

    for i in range(len(pyramid)-1):
        for j in range(len(pyramid[len(pyramid)-2-i])):
            pyramid[len(pyramid) - 2 - i][j] = max(pyramid[len(pyramid) - 2 - i][j]+pyramid[len(pyramid) - 1 - i][j],pyramid[len(pyramid) - 2 - i][j]+pyramid[len(pyramid) - 1 - i][j+1])
    return pyramid[0][0] 
```

思路：
比如：
3
7 4
2 4 6
8 5 9 3

从倒数第2行起 [2,4,6]
2+8>2+5
则用2+8=10代替2，以此类推
=》则倒数第2行变成[10,13,15]

金字塔变成：
3
7,4
10,13,15
8 ，5 ，9 ，3
然后向上计算。
[7,4] =》[20,19]

金字塔变成
3
20,19
10,13,15
8 ，5 ，9 ，3

最后计算第一行，
金字塔变成：
23
20,19
10,13,15
8 ，5 ，9 ，3

返回pyramid[0][0]

更优解：

```
def longest_slide_down(p):
    res = p.pop()
    while p:
        tmp = p.pop()
        res = [tmp[i] + max(res[i],res[i+1])  for i in range(len(tmp))] 
    return res.pop() 
```