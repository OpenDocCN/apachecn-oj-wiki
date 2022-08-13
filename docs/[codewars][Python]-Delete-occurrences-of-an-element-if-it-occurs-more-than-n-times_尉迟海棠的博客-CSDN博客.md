<!--yml
category: codewars
date: 2022-08-13 11:52:15
-->

# [codewars][Python] Delete occurrences of an element if it occurs more than n times_尉迟海棠的博客-CSDN博客

> 来源：[https://blog.csdn.net/GYK0812/article/details/102783123?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-102783123.nonecase](https://blog.csdn.net/GYK0812/article/details/102783123?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-102783123.nonecase)

## Task

Given a list lst and a number N, create a new list that contains each number of lst at most N times without reordering. For example if N = 2, and the input is [1,2,3,1,2,1,2,3], you take [1,2,3,1,2], drop the next [1,2] since this would lead to 1 and 2 being in the result 3 times, and then take 3, which leads to [1,2,3,1,2,3].

## Example

```
 delete_nth ([1,1,1,1],2) # return [1,1]

  delete_nth ([20,37,20,21],1) # return [20,37,21]
```

```
def delete_nth(order,max_e):
    #去除列表中超过max_e次的元素
    list1 = []
    for x in order:
        if list1.count(x) <max_e:
            list1.append(x)

    return list1
```