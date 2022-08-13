<!--yml
category: codewars
date: 2022-08-13 11:31:27
-->

# Codewars第三天--Unique In Order_soufal的博客-CSDN博客

> 来源：[https://blog.csdn.net/u011562123/article/details/81156950?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-81156950.142^v40^control,185^v2^control](https://blog.csdn.net/u011562123/article/details/81156950?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-81156950.142^v40^control,185^v2^control)

Implement the function unique_in_order which takes as argument a sequence and returns a list of items without any elements with the same value next to each other and preserving the original order of elements.

For example:

unique_in_order(‘AAAABBBCCDAABBB’) == [‘A’, ‘B’, ‘C’, ‘D’, ‘A’, ‘B’]
unique_in_order(‘ABBCcAD’) == [‘A’, ‘B’, ‘C’, ‘c’, ‘A’, ‘D’]
unique_in_order([1,2,2,3,3]) == [1,2,3]

```
def unique_in_order(iterable):
    result = []
    if len(iterable) != 0:

        n = len(iterable)
        a = iterable[0]
        result.append(a)
        for i in range(1,n):
            if iterable[i] != result[len(result)-1]:
                result.append(iterable[i])
        return result
    else:
        return result
```

最好的方法：

```
def unique_in_order(iterable):
    result = []
    prev = None
    for char in iterable[0:]:
        if char != prev:
            result.append(char)
            prev = char
    return result
```