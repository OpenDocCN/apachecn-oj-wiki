<!--yml
category: codewars
date: 2022-08-13 11:45:31
-->

# CodeWars：Is it even?（8kyu）_@小小程的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_43358019/article/details/105280213?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-105280213.nonecase](https://blog.csdn.net/qq_43358019/article/details/105280213?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-105280213.nonecase)

#### 内容：

```
In this Kata we are passing a number (n) into a function.

Your code will determine if the number passed is even (or not).

The function needs to return either a true or false.

Numbers may be positive or negative, integers or floats.

Floats are considered UNeven for this kata. 
```

#### 解决方案：python

**方法一：**

```
(1)
def is_even(n): 
    if n % 2 == 0:
        return True
    else:
        return False

(2)
def is_even(n): 
    output = False
    if n % 2 == 0:
        output = True
    return output 
```

**方法二:**

```
(1)
def is_even(n): 
    return False if type(n) == float or n % 2 != 0 else True

(2)
def is_even(n):
    return True if n % 2 ==0 else False

(3)
def is_even(n): 
    return (isinstance(n,int) and n % 2 == 0) 
```

**方法三：**

```
(1)
is_even = lambda n: n % 2 == 0

(2)
is_even = lambda x : not x % 2

(3)
is_even=lambda x : x%2==0

(4)
is_even=lambda x : True if x%2==0 else False 
```