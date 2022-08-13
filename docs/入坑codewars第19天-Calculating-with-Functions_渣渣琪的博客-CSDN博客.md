<!--yml
category: codewars
date: 2022-08-13 11:51:51
-->

# 入坑codewars第19天-Calculating with Functions_渣渣琪的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_37341950/article/details/85158739?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-85158739.nonecase](https://blog.csdn.net/sinat_37341950/article/details/85158739?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-85158739.nonecase)

题目：

This time we want to write calculations using functions and get the results. Let's have a look at some examples:

JavaScript:

```
seven(times(five())); // must return 35
four(plus(nine())); // must return 13
eight(minus(three())); // must return 5
six(dividedBy(two())); // must return 3 
```

Ruby:

```
seven(times(five)) # must return 35
four(plus(nine)) # must return 13
eight(minus(three)) # must return 5
six(divided_by(two)) # must return 3
```

题意：

```
题意看输出样例就知道；
seven(times(five)) # must return 35
seven=7
times=*
five=5
7*5=35
```

思路：

```
我的思路是
比如zero（a）函数
如果a传入的是0则返回0
否则返回+、-、*、/ a，见下面代码
而对于times（a）则说明是返回 *a
见代码。
```

代码：我的代码很好理解，就是太冗余了，不太好，待会看大神的精简代码~

```
def zero(a='0'):
    if a != '0':
        if a[0]=='+':
            return 0+int(a[1])
        if a[0]=='-':
            return 0-int(a[1])
        if a[0]=='*':
            return 0*int(a[1])
        if a[0]=='/':
            return int(0/int(a[1]))
    else:
        return '0'
def one(a='1'):
    if a != '1':
        if a[0]=='+':
            return 1+int(a[1])
        if a[0]=='-':
            return 1-int(a[1])
        if a[0]=='*':
            return 1*int(a[1])
        if a[0]=='/':
            return int(1/int(a[1]))
    else:
        return '1'
def two(a='2'):
    if a != '2':
        if a[0]=='+':
            return 2+int(a[1])
        if a[0]=='-':
            return 2-int(a[1])
        if a[0]=='*':
            return 2*int(a[1])
        if a[0]=='/':
            return int(2/int(a[1]))
    else:
        return '2'
def three(a='3'):
    if a != '3':
        if a[0]=='+':
            return 3+int(a[1])
        if a[0]=='-':
            return 3-int(a[1])
        if a[0]=='*':
            return 3*int(a[1])
        if a[0]=='/':
            return int(3/int(a[1]))
    else:
        return '3'
def four(a='4'):
    if a != '4':
        if a[0]=='+':
            return 4+int(a[1])
        if a[0]=='-':
            return 4-int(a[1])
        if a[0]=='*':
            return 4*int(a[1])
        if a[0]=='/':
            return int(4/int(a[1]))
    else:
        return '4'
def five(a='5'):
    if a != '5':
        if a[0]=='+':
            return 5+int(a[1])
        if a[0]=='-':
            return 5-int(a[1])
        if a[0]=='*':
            return 5*int(a[1])
        if a[0]=='/':
            return int(5/int(a[1]))
    else:
        return '5'
def six(a='6'):
    if a != '6':
        if a[0]=='+':
            return 6+int(a[1])
        if a[0]=='-':
            return 6-int(a[1])
        if a[0]=='*':
            return 6*int(a[1])
        if a[0]=='/':
            return int(6/int(a[1]))
    else:
        return '6'
def seven(a='7'):
    if a != '7':
        if a[0]=='+':
            return 7+int(a[1])
        if a[0]=='-':
            return 7-int(a[1])
        if a[0]=='*':
            return 7*int(a[1])
        if a[0]=='/':
            return int(7/int(a[1]))
    else:
        return '7'
def eight(a='8'):
    if a != '8':
        if a[0]=='+':
            return 8+int(a[1])
        if a[0]=='-':
            return 8-int(a[1])
        if a[0]=='*':
            return 8*int(a[1])
        if a[0]=='/':
            return int(8/int(a[1]))
    else:
        return '8'
def nine(a='9'):
    if a != '9':
        if a[0]=='+':
            return 9+int(a[1])
        if a[0]=='-':
            return 9-int(a[1])
        if a[0]=='*':
            return 9*int(a[1])
        if a[0]=='/':
            return int(9/int(a[1]))
    else:
        return '9'

def plus(a):
    return '+'+a
def minus(a):
    return '-'+a
def times(a):
    return '*'+a
def divided_by(a):
    return '/'+a
```

看看大神的代码吧，厉害就是厉害，lambda表达式用的六，我就没想到

```
def zero(f = None): return 0 if not f else f(0)
def one(f = None): return 1 if not f else f(1)
def two(f = None): return 2 if not f else f(2)
def three(f = None): return 3 if not f else f(3)
def four(f = None): return 4 if not f else f(4)
def five(f = None): return 5 if not f else f(5)
def six(f = None): return 6 if not f else f(6)
def seven(f = None): return 7 if not f else f(7)
def eight(f = None): return 8 if not f else f(8)
def nine(f = None): return 9 if not f else f(9)

def plus(y): return lambda x: x+y
def minus(y): return lambda x: x-y
def times(y): return lambda  x: x*y
def divided_by(y): return lambda  x: x/y
```