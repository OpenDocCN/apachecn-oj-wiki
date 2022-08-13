<!--yml
category: codewars
date: 2022-08-13 11:39:45
-->

# Python练习题答案: 约翰和安报名参加Codewars【难度：3级】--景越Python编程实例训练营,1000道上机题等你来挑战_景越的博客-CSDN博客

> 来源：[https://blog.csdn.net/aumtopsale/article/details/102774760?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-4-102774760-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/aumtopsale/article/details/102774760?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-4-102774760-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## 约翰和安报名参加Codewars【难度:3级】:

# 答案1:

```
def j_n(n):
    j = [0]
    a = [1]
    for i in range(1, n):
        j.append((i - a[j[i-1]]))
        a.append((i-j[a[i-1]]))
    return j, a

def john(n):
    return j_n(n)[0]

def ann(n):
    return j_n(n)[1]

def sum_john(n):
    return sum(john(n))

def sum_ann(n):
   return sum(ann(n))​ 
```

# 答案2:

```
from functools import lru_cache

@lru_cache(maxsize = None)
def john_value(n):
    if n == 0:
        return 0
    return n - ann_value(john_value(n - 1))

@lru_cache(maxsize = None)
def ann_value(n):
    if n == 0:
        return 1
    return n - john_value(ann_value(n - 1))

def ann(n):
    return [ann_value(x) for x in range(n)]

def john(n):
    return [john_value(x) for x in range(n)]

def sum_john(n):
    return sum(john(n))

def sum_ann(n):
    return sum(ann(n))​ 
```

# 答案3:

```
def get_arrays(n, name):
    a = [1]
    j = [0]
    for i in xrange(1, n):
        next_j = i - a[j[i-1]]
        j.append(next_j)
        next_a = i - j[a[i-1]]
        a.append(next_a)
    ret = {
        'john': j,
        'ann' : a
    }
    return ret[name]

def john(n):
    return get_arrays(n, 'john')

def ann(n):
    return get_arrays(n, 'ann')

def sum_john(n):
    return sum(john(n))

def sum_ann(n):
    return sum(ann(n))​ 
```

# 答案4:

```
def generate_solved_练习题(n):
    """ 生成ann和john在第n天时的解题数量表"""
    john_练习题 = [0]
    ann_练习题 = [1]
    for i in range(1, n):
        john_练习题.append(i - ann_练习题[john_练习题[i-1]])
        ann_练习题.append(i - john_练习题[ann_练习题[i-1]])
    return john_练习题, ann_练习题

def john(n):
    return generate_solved_练习题(n)[0]

def ann(n):
    return generate_solved_练习题(n)[1]

def sum_john(n):
    return sum(john(n))

def sum_ann(n):
    return sum(ann(n))​ 
```

# 答案5:

```
def john_and_ann(n):
    john = [0]
    ann = [1]
    for i in range(1, n):
        t1, t2 = ann[i-1],  john[i-1]
        john.append(i - ann[t2])
        ann.append(i - john[t1])
    return john, ann

def ann(n):
    john, ann = john_and_ann(n)
    return ann

def john(n):
    john, ann = john_and_ann(n)
    return john

def sum_ann(n):
    Ann = ann(n)
    return sum(Ann)

def sum_john(n):
    John = john(n)
    return sum(John)​ 
```

# 答案6:

```
jm, am = {0:0}, {0:1}
def j(n):
    if n in jm.keys(): return jm[n]
    jm[n] = n - a(j(n-1))
    return jm[n]

def a(n):
    if n in am.keys(): return am[n]
    am[n] = n - j(a(n-1))
    return am[n]

def john(n):
    return [j(i) for i in range(n)]

def ann(n):
    return [a(i) for i in range(n)]

def sum_john(n):
    return sum(john(n))

def sum_ann(n):
    return sum(ann(n))​ 
```

# 答案7:

```
 john_dict = {}
ann_dict = {}

def john_val(n):
    if n == 0:
        return 0
    if not n in john_dict:
        john_dict[n] =  n - ann_val(john_val(n-1))
    return john_dict[n]

def ann_val(n):
    if n == 0:
        return 1
    if not n in ann_dict:
        ann_dict[n] =  n - john_val(ann_val(n-1))
    return ann_dict[n]

def john(n):
    return [john_val(i) for i in range(n)]

def ann(n):
    return [ann_val(i) for i in range(n)]

def sum_john(n):
    return sum(john(n))

def sum_ann(n):
    return sum(ann(n))
​ 
```

# 答案8:

```
def johnann(n, jnota):
    j, a = [0], [1]
    for i in range(1,n):
        j.append(i-a[j[-1]])
        a.append(i-j[a[-1]])
    return j if jnota else a

john = lambda n: johnann(n, True)
ann = lambda n: johnann(n, False)
sum_john = lambda n: sum(john(n))
sum_ann = lambda n: sum(ann(n))
​ 
```

# 答案9:

```
from functools import lru_cache

@lru_cache(None)
def a(n):
    if n == 0:
        return 1
    return n - j(a(n - 1))

@lru_cache(None)
def j(n):
    if n == 0:
        return 0
    return n - a(j(n - 1))

def ann(n):
    return [a(i) for i in range(n)]

def john(n):
    return [j(i) for i in range(n)]

def sum_john(n):
    return sum(john(n))

def sum_ann(n):
    return sum(ann(n))​ 
```

# 答案10:

```
j = [0]
a = [1]

def fill(n):
    for d in range(len(a), n):
        j.append(d - a[j[d - 1]])
        a.append(d - j[a[d - 1]])

def john(n):
    fill(n)
    return j[:n]

def ann(n):
    fill(n)
    return a[:n]

def sum_john(n):
    return sum(john(n))

def sum_ann(n):
    return sum(ann(n))
​ 
```

[![Python基础训练营](img/9ddc589a9bae9dd81334056da3504a2c.png "Python基础训练营")景越Python基础训练营QQ群](//shang.qq.com/wpa/qunwpa?idkey=c10499c0a2daa9cc444ea9695745b4919a58202d6abdc107e1ed42882d604d5b)

![在这里插入图片描述](img/7212073a4e753731a08f404f4ada9768.png)
欢迎各位同学加群讨论,一起学习,共同成长!