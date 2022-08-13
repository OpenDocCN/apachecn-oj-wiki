<!--yml
category: codewars
date: 2022-08-13 11:50:11
-->

# [codewars][python]Total amount of points_sjtubn的博客-CSDN博客

> 来源：[https://blog.csdn.net/sjtubn/article/details/87693676?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-87693676.nonecase](https://blog.csdn.net/sjtubn/article/details/87693676?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-87693676.nonecase)

Our football team finished the championship. The result of each match look like "x:y". Results of all matches are recorded in the collection.

For example: `["3:1", "2:2", "0:1", ...]`

Write a function that takes such collection and counts the points of our team in the championship. Rules for counting points for each match:

*   if x>y - 3 points
*   if x<y - 0 point
*   if x=y - 1 point

Notes:

*   there are 10 matches in the championship
*   0 <= x <= 4
*   0 <= y <= 4

思路：遍历所有的比赛，截取字符串比较分数大小，然后累计。

代码如下：

def points(games):
    n=0
    for i in games:
        temp = i.split(':')
        n1=int(temp[0])
        n2=int(temp[1])
        if n1>n2:
            n+=3
        elif n1==n2:
            n+=1
    return n