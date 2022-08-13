<!--yml
category: codewars
date: 2022-08-13 11:26:03
-->

# codewars【1】_幻梦鸵鸟的博客-CSDN博客

> 来源：[https://blog.csdn.net/i897355249/article/details/99068866?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-99068866.142^v40^control,185^v2^control](https://blog.csdn.net/i897355249/article/details/99068866?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-99068866.142^v40^control,185^v2^control)

今天开始记录自己在codewars上遇到的问题和得到的收获。
首先是自己已完成的四道题。
**1.CreditCardMask**
Usually when you buy something, you’re asked whether your credit card number, phone number or answer to your most secret question is still correct. However, since someone could look over your shoulder, you don’t want that shown on your screen. Instead, we mask it.
Your task is to write a function maskify, which changes all but the last four characters into ‘#’.
Examples：

```
maskify("4556364607935616") == "############5616"
maskify(     "64607935616") ==      "#######5616"
maskify(               "1") ==                "1"
maskify(                "") ==                 ""

# "What was the name of your first pet?"
maskify("Skippy")                                   == "##ippy"
maskify("Nananananananananananananananana Batman!") == "####################################man!" 
```

My solution：

```
# return masked string
def maskify(cc):
    s=list(cc)
    l=len(cc)
    if (l-4)>0:
        for i in range(l-4):
            s[i]='#'
    p=''.join(s)
    return p
    pass 
```

Clever solution NO.1：

```
# return masked string
def maskify(cc):
    return "#"*(len(cc)-4) + cc[-4:] 
```

Clever solution NO.2：

```
# return masked string
def maskify(cc):
    return '{message:#>{fill}}'.format(message=cc[-4:], fill=len(cc)) 
```

**2.Beginner Series #3 Sum of Numbers**
Given two integers a and b, which can be positive or negative, find the sum of all the numbers between including them too and return it. If the two numbers are equal return a or b.
Note: a and b are not ordered!
Examples:

```
get_sum(1, 0) == 1   // 1 + 0 = 1
get_sum(1, 2) == 3   // 1 + 2 = 3
get_sum(0, 1) == 1   // 0 + 1 = 1
get_sum(1, 1) == 1   // 1 Since both are same
get_sum(-1, 0) == -1 // -1 + 0 = -1
get_sum(-1, 2) == 2  // -1 + 0 + 1 + 2 = 2 
```

My solution:

```
def get_sum(a,b):
    #good luck!
    sum=0
    if a==b:
        return a
    else:
        if a<b:
            for i in range(a,b+1):
                sum=sum+i
        if a>b:
            for i in range(b,a+1):
                sum=sum+i
        return sum 
```

Clever solution NO.1：

```
def get_sum(a,b):
    return sum(xrange(min(a,b), max(a,b)+1)) 
```

*此题需要注意，Note: a and b are not ordered!这句话指出a与b并未排序好，a可能比b大，需要考虑到这种情况，我未能考虑周全，因此出错。*
**3.Highest and Lowest**
In this little assignment you are given a string of space separated numbers, and have to return the highest and lowest number.
Notes:
All numbers are valid Int32, no need to validate them.
There will always be at least one number in the input string.
Output string must be two numbers separated by a single space, and highest number is first.
Examples：

```
high_and_low("1 2 3 4 5")  # return "5 1"
high_and_low("1 2 -3 4 5") # return "5 -3"
high_and_low("1 9 3 4 -5") # return "9 -5" 
```

My solution:

```
def high_and_low(numbers):
        # ...
        s=numbers.split()
        s=[int(x) for x in s]
        p=[]
        p.append(max(s))
        p.append(min(s))
        numbers=' '.join([str(i) for i in p])
        return numbers 
```

Clever solution NO.1:

```
def high_and_low(numbers): #z.
    nn = [int(s) for s in numbers.split(" ")]
    return "%i %i" % (max(nn),min(nn)) 
```

Clever solution NO.2:

```
def high_and_low(numbers):
  n = map(int, numbers.split(' '))
  return str(max(n)) + ' ' + str(min(n)) 
```

*此题学习到了split()函数的使用方法：*

```
str.split(str="", num=string.count(str)). 
```

*str – 分隔符，默认为所有的空字符，包括空格、换行(\n)、制表符(\t)等。
num – 分割次数。默认为 -1, 即分隔所有。*

*同时，max()函数应用到列表时，如列表内都是字符串，那么比较的是ASC码值，无法准确比较数字大小，若需要比较数字字符串的数字大小，需要使用*

```
s=[int(x) for x in s] 
```

*将数字字符串的引号去掉，同理可使用*

```
s=[str(x) for x in s] 
```

*将数字重新转化为数字字符串*
**4.Exes and Ohs**
Check to see if a string has the same amount of 'x’s and 'o’s. The method must return a boolean and be case insensitive. The string can contain any char.
Examples input/output:

```
XO("ooxx") => true
XO("xooxx") => false
XO("ooxXm") => true
XO("zpzpzpp") => true // when no 'x' and 'o' is present should return true
XO("zzoo") => false 
```

My solution：

```
def xo(s):
    i=s.count('o')
    k=s.count('O')
    j=s.count('x')
    p=s.count('X')
    if (i+k)==(j+p):
        return True
    else:
        return False 
```

Clever solution NO1:

```
def xo(s):
    s = s.lower()
    return s.count('x') == s.count('o') 
```

*此题注意点在大小写字母都可以识别，be case insensitive！*

至此四题如上，任重道远！