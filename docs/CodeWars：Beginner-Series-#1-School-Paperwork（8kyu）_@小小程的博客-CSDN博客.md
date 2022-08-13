<!--yml
category: codewars
date: 2022-08-13 11:45:40
-->

# CodeWars：Beginner Series #1 School Paperwork（8kyu）_@小小程的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_43358019/article/details/105256543?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-105256543.nonecase](https://blog.csdn.net/qq_43358019/article/details/105256543?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-105256543.nonecase)

#### 内容：

```
Your classmates asked you to copy some paperwork for them.
You know that there are 'n' classmates and the paperwork has 'm' pages.

Your task is to calculate how many blank pages do you need.

Example:
paperwork(5, 5) == 25
Note: if n < 0 or m < 0 return 0! 
```

#### 解决方案：python

**方法一：**

```
（1）
def paperwork(n, m):
    if (n<0 or m<0):
        return 0
    else :
        return n*m

（2）
def paperwork(n, m):
    if m > 0 and n > 0:
        return m*n
    else:
        return 0 
```

**方法二：**

```
def paperwork(n, m):
    return max(n, 0)*max(m, 0) 
```

**方法三：**

```
paperwork = lambda m,n: m*n if m>0 and n>0 else 0 
```

**方法四:**

```
def paperwork(n, m):
    return n*m if n>=0 and m>=0 else 0 
```