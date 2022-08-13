<!--yml
category: codewars
date: 2022-08-13 11:39:27
-->

# codewars2 Shortest Word_z_y_ning的博客-CSDN博客

> 来源：[https://blog.csdn.net/z_y_ning/article/details/102503418?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-26-102503418-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/z_y_ning/article/details/102503418?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-26-102503418-null-null.142^v40^control,185^v2^control&utm_term=codewars)

**Instructions**
Simple, given a string of words, return the length of the shortest word(s).

String will never be empty and you do not need to account for different data types.
**solution:**

```
def find_short(s):
    l=100
    for word in s.split():
        l=min(len(word),l)
    return l 
```