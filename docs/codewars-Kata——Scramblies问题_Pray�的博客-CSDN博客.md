<!--yml
category: codewars
date: 2022-08-13 11:42:54
-->

# codewars Kata——Scramblies问题_Pray�的博客-CSDN博客

> 来源：[https://blog.csdn.net/Pray_21/article/details/112135556?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-28-112135556-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/Pray_21/article/details/112135556?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-28-112135556-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 代码

代码的关键点在于巧妙利用python的Counter函数，见下

```
 """
codewars Kata: Scramblies

Created on Sun Jan  3 14:58:48 2021

@author: Pray
"""

s1 = 'katas'
s2 = 'steak'

from collections import Counter  
def scramble(s1, s2):
    return len(Counter(s2) - Counter(s1)) == 0

print(scramble(s1, s2)) 
```