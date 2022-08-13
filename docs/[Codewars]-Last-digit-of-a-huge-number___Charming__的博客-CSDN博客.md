<!--yml
category: codewars
date: 2022-08-13 11:46:28
-->

# [Codewars]-Last digit of a huge number___Charming__的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41882147/article/details/81065521?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-81065521.nonecase](https://blog.csdn.net/qq_41882147/article/details/81065521?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-81065521.nonecase)

### 超级大的数字的最后一位数字（python）

#### 题目：

这个跟普通的大数取模（快速幂取模）有一点点不一样，这个题目是多次取幂

例如：给出一个数组（列表）`[x1, x2, x3, ..., xn]`，你需要找到`x1 ^ (x2 ^ (x3 ^ (... ^ xn)))`这个大数的最后一位数字

#### 思路：

细心观察每个个位数的倍数的对10求余数，会发现以下规律

```
0:[0,0,0,0],
1:[1,1,1,1],
2:[2,4,8,6],
3:[3,9,7,1],
4:[4,6,4,6],
5:[5,5,5,5],
6:[6,6,6,6],
7:[7,9,3,1],
8:[8,4,2,6],
9:[9,1,9,1]
```

每个个位数的倍数的对10求余数，都是符合以4为周期的循环
于是只要指数对4求与即可。
然后一层一层计算

#### 解答：

```
def last_digit(lst):
    n = 1
    for x in reversed(lst):

        n = x ** (n if n < 4 else n % 4 + 4) 
    return n % 10
```

#### 类似的题目：

[[Codewars]-Last digit of a large number](https://blog.csdn.net/qq_41882147/article/details/81029486)