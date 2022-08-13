<!--yml
category: codewars
date: 2022-08-13 11:29:22
-->

# codewars4_shitfly的博客-CSDN博客

> 来源：[https://blog.csdn.net/s969966195/article/details/72331192/?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-72331192.142^v40^control,185^v2^control](https://blog.csdn.net/s969966195/article/details/72331192/?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-72331192.142^v40^control,185^v2^control)

**Recover a secret string from random triplets**

```
def recoverSecret(triplets):
    res=''
    while triplets!=[]:
        non_firsts=[num for t in triplets for num in t[1:]]
        firsts=[t[0] for t in triplets]
        for f in firsts:
            if f not in non_firsts:
                res+=f
                for t in triplets:
                    if t[0]==f:
                        t.pop(0)
                break
        triplets=[t for t in triplets if t!=[]]
    return res
```

每次可以确定谁在最前面

```
def recoverSecret(triplets):
  r = list(set([i for l in triplets for i in l]))
  for l in triplets:
    fix(r, l[1], l[2])
    fix(r, l[0], l[1])
  return ''.join(r)

def fix(l, a, b):
   """let l.index(a) < l.index(b)"""
   if l.index(a) > l.index(b):
       l.remove(a)
       l.insert(l.index(b), a)
```

判断每个子列表中先后顺序，将其在r列表中的位置按子列表中排好，但是若原列表中有重复元素，set()会把重复的元素去除
**Getting along with Integer Partitions**
这道题原意是输入一个整数，然后将其分解为若干个数字的和，例如：

5 = 5
5 = 4 + 1
·
·
·
5 = 1 + 1 + 1 + 1 + 1
于是这样就形成了一个集合：

enum(5)-> [[5],[4,1],[3,2],[3,1,1],[2,2,1],[2,1,1,1],[1,1,1,1,1]]
接下来计算每个子集合的积（product），并去重、排序，于是得到：

prod(5) -> [1,2,3,4,5,6]
接下来就是求这个数组中的极差、平均数和中位数了