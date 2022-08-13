<!--yml
category: codewars
date: 2022-08-13 11:48:48
-->

# Codewars第四天--Two to One_soufal的博客-CSDN博客

> 来源：[https://blog.csdn.net/u011562123/article/details/81171484?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-81171484.nonecase](https://blog.csdn.net/u011562123/article/details/81171484?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-81171484.nonecase)

## Codewars第四天–Two to One

题目描述：
`Take 2 strings s1 and s2 including only letters from ato z. Return a new sorted string, the longest possible, containing distinct letters,
each taken only once - coming from s1 or s2\. #Examples: a = "xyaabbbccccdefww" b = "xxxxyyyyabklmopq" longest(a, b) -> "abcdefklmopqwxy"
a = "abcdefghijklmnopqrstuvwxyz" longest(a, a) -> "abcdefghijklmnopqrstuvwxyz"`

想的思路是将字符串合并为一个，然后依次判断加入到一个新的列表中，然后得到没有重复字符的列表，对其排序转换输出即可。代码如下：

```
def longest(s1, s2):

    z = s1 + s2
    result = []
    for i in z:
        if i not in result:
            result.append(i)
    result.sort()
    return "".join(result)
```

*遇到的问题，在使用`"".join()` 将列表转换为字符串的过程中，开始使用了`"".join(result.soirt())` 语句，出现了类型错误：

```
TypeError: can only join an iterable
```

原因是join里面不能出现函数，需要单独提出了排序后，再使用join进行操作。

最佳做法：

```
def longest(a1, a2):
    return "".join(sorted(set(a1 + a2)))
```

使用sorted进行排序，set()可以创建一个无序不重复元素集，这样就起到了去重作用。