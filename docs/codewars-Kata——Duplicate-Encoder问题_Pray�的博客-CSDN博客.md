<!--yml
category: codewars
date: 2022-08-13 11:45:42
-->

# codewars Kata——Duplicate Encoder问题_Pray�的博客-CSDN博客

> 来源：[https://blog.csdn.net/Pray_21/article/details/109892037?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-109892037.nonecase](https://blog.csdn.net/Pray_21/article/details/109892037?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-109892037.nonecase)

# 大致思路

利用字典dict数据结构，将字符串中的字符与该字符出现的次数建立一一对应的映射关系，通过遍历字符串检视每一字符出现的次数来决定生成新字符的内容

# 代码

```
 """
Kata Duplicate Encoder

Created on Sat Nov 21 10:11:07 2020

@author: Pray
"""

def duplicate_encode(word):

    newword=[]                  
    d = dict()                  
    word = word.lower()         

    for x in word:
        if x not in d.keys():
            d[x] = 1
        else:
            d[x] = d[x] + 1

    for i in word:
        if(d[i] > 1):
            newword.append(')')
        else:
            newword.append('(')
    newword = ''.join(newword)  
    return newword 
```