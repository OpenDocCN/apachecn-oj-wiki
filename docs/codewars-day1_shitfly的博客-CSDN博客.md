<!--yml
category: codewars
date: 2022-08-13 11:40:24
-->

# codewars day1_shitfly的博客-CSDN博客

> 来源：[https://blog.csdn.net/s969966195/article/details/70257374?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-17-70257374-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/s969966195/article/details/70257374?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-17-70257374-null-null.142^v40^control,185^v2^control&utm_term=codewars)

**1.Find The Parity Outlier**
Description:

You probably know the “like” system from Facebook and other pages. People can “like” blog posts, pictures or other items. We want to create the text that should be displayed next to such an item.

Implement a function likes :: [String] -> String, which must take in input array, containing the names of people who like an item. It must return the display text as shown in the examples:

```
likes [] // must be "no one likes this"
likes ["Peter"] // must be "Peter likes this"
likes ["Jacob", "Alex"] // must be "Jacob and Alex like this"
likes ["Max", "John", "Mark"] // must be "Max, John and Mark like this"
likes ["Alex", "Jacob", "Mark", "Max"] // must be "Alex, Jacob and 2 others like this"
```

For more than 4 names, the number in and 2 others simply increases.

My answer:

```
def likes(names):
    length=len(names)
    if length==0:
        return 'no one likes this'
    elif length==1:
        return '%s likes this' % names[0]
    elif length==2:
        return '%s and %s like this' % (names[0],names[1])
    elif length==3:
        return '%s, %s and %s like this' % (names[0],names[1],names[2])
    else:
        return '%s, %s and %d others like this' % (names[0],names[1],length-2)
```

good anstwer:

```
def likes(names):
    n = len(names)
    return {
        0: 'no one likes this',
        1: '{} likes this', 
        2: '{} and {} like this', 
        3: '{}, {} and {} like this', 
        4: '{}, {} and {others} others like this
    }[min(4, n)].format(*names[:3], others=n-2)
```

format通过{}和:来代替%。以后尝试用format来替代%

**2.Find The Parity Outlier**
Description:

You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns N.

For example:

[2, 4, 0, 100, 4, 11, 2602, 36]

Should return: 11

[160, 3, 1719, 19, 11, 13, -21]

Should return: 160
我写的好蠢：

```
def find_it(integers,temp):
    if temp==1:
        for i in integers:
            if i%2==0:
                return i
    else:
        for i in integers:
            if i%2==1:
                return i

def find_outlier(integers):
    if integers[0]%2==integers[1]%2==0:
        return find_it(integers,1)
    elif integers[0]%2==integers[1]%2==1:
        return find_it(integers,0)
    else:
        if integers[2]%2==0:
            return find_it(integers,1)
        else:
            return find_it(integers, 0)
```

可以统计奇数和偶数的数量，返回数量为1的
x if x < y else y:如果x < y返回x，否则返回y