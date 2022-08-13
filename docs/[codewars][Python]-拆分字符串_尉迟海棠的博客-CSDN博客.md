<!--yml
category: codewars
date: 2022-08-13 11:52:04
-->

# [codewars][Python] 拆分字符串_尉迟海棠的博客-CSDN博客

> 来源：[https://blog.csdn.net/gyk0812/article/details/102801669?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-102801669.nonecase](https://blog.csdn.net/gyk0812/article/details/102801669?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-102801669.nonecase)

题目：

Complete the solution so that it splits the string into pairs of two characters. If the string contains an odd number of characters then it should replace the missing second character of the final pair with an underscore ('_').

Examples:

```
solution('abc') # should return ['ab', 'c_']
solution('abcdef') # should return ['ab', 'cd', 'ef']
```

My Answer:

思路：如果长度是奇数，就在字符串后面添加一个“_”

```
def solution(s):
    list1 = []
    for i in range(len(s)):
        if len(s) %2 !=0:
            s = s + "_"
            print(s)
        if i % 2 == 0:
            list1.append(s[i:i + 2])

    return list1
```

Smart Answer:

思路：使用正则表达式

```
import re

def solution(s):
    return re.findall(".{2}", s + "_")
#用正则表达式来返回所有结果组成的列表，实在太巧妙了
#先把s后面加上“_”,输出时，2个字母为单位输出，如果s的长度是奇数，则“_”不会被输出
```