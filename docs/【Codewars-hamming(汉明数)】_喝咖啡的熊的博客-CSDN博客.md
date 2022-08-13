<!--yml
category: codewars
date: 2022-08-13 11:45:24
-->

# 【Codewars-hamming(汉明数)】_喝咖啡的熊的博客-CSDN博客

> 来源：[https://blog.csdn.net/crowhe1993/article/details/52863242?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-52863242.nonecase](https://blog.csdn.net/crowhe1993/article/details/52863242?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-52863242.nonecase)

【题目】
以2，3，5为底的汉明数，表示为**(2^i)*(3^j)*(5^k)**,其中i，j，k为大于等于0的整数。
即汉明数的第一个为(2^0)*(3^0)*(5^0) = 1，第二个为2，第三个为3，第四个为4……以此类推下去。
编写程序求第n个汉明数
【解】

```
def hamming(n):
    k1,k2,k3 = 0,0,0
    res = [1]
    for i in range(1,n):
        s1 = res[k1]*2
        s2 = res[k2]*3
        s3 = res[k3]*5
        min_val = min(s1,s2,s3)
        res.append(min_val)
        if res[i] == s1:
            k1 +=1
        if res[i] == s2:
            k2 += 1
        if res[i] == s3:
            k3+= 1
    return res[-1]
```