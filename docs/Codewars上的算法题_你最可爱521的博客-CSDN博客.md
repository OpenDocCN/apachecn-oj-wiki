<!--yml
category: codewars
date: 2022-08-13 11:36:40
-->

# Codewars上的算法题_你最可爱521的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_44184794/article/details/102883275?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-102883275.142^v40^control,185^v2^control](https://blog.csdn.net/qq_44184794/article/details/102883275?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-102883275.142^v40^control,185^v2^control)

# Codewars上的算法题

##### 1.新的《复仇者联盟》电影刚刚发行！电影票房里有很多人排成一列。他们每个人都有一个单一的100，50还是25美元的钞票。“复仇者”票的费用25 dollars。Vasya目前正在担任文员。他想向该行中的每个人卖票。如果Vasya最初没有钱并且严格按照人们排队的顺序卖票，可以给所有人卖票并找零吗？

###### 例子：

tickets([25, 25, 50]) # => YES
tickets([25, 100]) # => NO. Vasya will not have enough money to give change to 100 dollars
tickets([25, 25, 50, 50, 100]) # => NO. Vasya will not have the right bills to give 75 dollars of change (you can’t make two bills of 25 from one of 50)

###### 代码：

```
def tickets(people):
    m = {'25':0,'50':0,'75':0}
    for item in people:
      if item==25:
        m['25']+=1
      elif item==50:
        m['25']-=1
        m['50']+=1
        if m['25']<0:
          return 'NO'
      else:
        m['25']-=1
        m['50']-=1
        if m['25']<0 or m['50']<0:
          return 'NO'
    return 'YES' 
```