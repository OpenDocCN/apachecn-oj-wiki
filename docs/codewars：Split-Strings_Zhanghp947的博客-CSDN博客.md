<!--yml
category: codewars
date: 2022-08-13 11:43:17
-->

# codewars:Split Strings_Zhanghp947的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_44389971/article/details/104518343?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-104518343.nonecase](https://blog.csdn.net/weixin_44389971/article/details/104518343?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-104518343.nonecase)

# codewars:Split Strings

## Instructions

Complete the solution so that it splits the string into pairs of two characters. If the string contains an odd number of characters then it should replace the missing second character of the final pair with an underscore (’_’).

## Examples:

solution(‘abc’) # should return [‘ab’, ‘c_’]
solution(‘abcdef’) # should return [‘ab’, ‘cd’, ‘ef’]
solution(’’) # should return []

## 我的代码

这题我是用了递归的解法，递归就在于缩小问题的规模，同时有结束的最小条件。我个人觉得一遇到递归的问题脑子会先短路一下，这题最后是挺简单的，但我还是花了时间去捋的。

```
def solution(s):    
    if len(s)<=1:
        if len(s)==0:
            return []
        else:
            return [s+'_']
    return [s[0:2]]+solution(s[2:])
```