<!--yml
category: codewars
date: 2022-08-13 11:51:47
-->

# 【Codewars python 6kyu】: Split Strings_小菜鸟快飞的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36362028/article/details/100547161?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-100547161.nonecase](https://blog.csdn.net/qq_36362028/article/details/100547161?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-100547161.nonecase)

# 问题描述：

Complete the solution so that it splits the string into pairs of two characters. If the string contains an odd number of characters then it should replace the missing second character of the final pair with an underscore ('_').

Examples:

```
solution('abc') # should return ['ab', 'c_']
solution('abcdef') # should return ['ab', 'cd', 'ef']
```

# 代码实现：

```
#codewars第七题
def solution(s):
    ss = []
    _length = len(s)
    if _length%2 == 0:
        for i in range(0,_length,2):
            ss.append(s[i:i+2])
    else:
        for i in range(0,_length-1,2):
            ss.append(s[i:i+2])
        if _length == 1:
            ss.append(s[0] + '_')
        else:
            ss.append(s[i+2] + '_')
    return ss

#另解一
import re
def solution(s):
    return re.findall(".{2}", s + "_")

#另解二
def solution(s):
    result = []
    if len(s) % 2:
        s += '_'
    for i in range(0, len(s), 2):
        result.append(s[i:i+2])
    return result
```