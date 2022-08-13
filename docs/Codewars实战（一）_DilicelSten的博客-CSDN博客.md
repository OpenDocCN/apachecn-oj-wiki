<!--yml
category: codewars
date: 2022-08-13 11:43:15
-->

# Codewars实战（一）_DilicelSten的博客-CSDN博客

> 来源：[https://blog.csdn.net/Totoro1745/article/details/87621627?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-87621627.nonecase](https://blog.csdn.net/Totoro1745/article/details/87621627?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-87621627.nonecase)

这是一个好网站，边刷题边补足自己的短板，下面会总结并选取最佳的解题方式，持续更新！（依据难度改变更新速度）

#### 题1 Credit Card Mask

Your task is to write a function maskify, which changes all but the last four characters into ‘#’
maskify(“4556364607935616”) == “############5616”
maskify( “64607935616”) == “#######5616”
maskify( “1”) == “1”
maskify( “”) == “”

```
def maskify(cc):
    return "#"*(len(cc)-4) + cc[-4:] 
```

#### 题2 You’re a square!

Given an integral number, determine if it’s a square number

```
import math
def is_square(n):
    if n >= 0:
        a = int(math.sqrt(n))
        return n == a * a
    else:
        return False 
```

#### 题3 Who likes it?

likes [] // must be “no one likes this”
likes [“Peter”] // must be “Peter likes this”
likes [“Jacob”, “Alex”] // must be “Jacob and Alex like this”
likes [“Max”, “John”, “Mark”] // must be “Max, John and Mark like this”
likes [“Alex”, “Jacob”, “Mark”, “Max”] // must be “Alex, Jacob and 2 others like this”

```
def likes(names):
    n = len(names)
    return {
        0: 'no one likes this',
        1: '{} likes this', 
        2: '{} and {} like this', 
        3: '{}, {} and {} like this', 
        4: '{}, {} and {others} others like this'
    }[min(4, n)].format(*names[:3], others=n-2) 
```

#### 题4 Bit Counting

Write a function that takes an integer as input, and returns the number of bits that are equal to one in the binary representation of that number. You can guarantee that input is non-negative.
Example: The binary representation of 1234 is 10011010010, so the function should return 5 in this case

```
def countBits(n):
    return bin(n).count("1") 
```

#### 题5 Format a string of names like ‘Bart, Lisa & Maggie’.

Given: an array containing hashes of names
Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.
Example:
namelist([ {‘name’: ‘Bart’}, {‘name’: ‘Lisa’}, {‘name’: ‘Maggie’} ])
returns ‘Bart, Lisa & Maggie’
namelist([ {‘name’: ‘Bart’}, {‘name’: ‘Lisa’} ])
returns ‘Bart & Lisa’
namelist([ {‘name’: ‘Bart’} ])
returns ‘Bart’
namelist([])
returns ‘’

```
def namelist(names):
    if len(names) > 1:
        return '{} & {}'.format(', '.join(name['name'] for name in names[:-1]), 
                                names[-1]['name'])
    elif names:
        return names[0]['name']
    else:
        return '' 
```

#### 题6 Sum of Digits / Digital Root

A digital root is the recursive sum of all the digits in a number. Given n, take the sum of the digits of n. If that value has two digits, continue reducing in this way until a single-digit number is produced. This is only applicable to the natural numbers.
digital_root(942)
=> 9 + 4 + 2
=> 15 …
=> 1 + 5
=> 6

```
def digital_root(n):
    while n >= 10:
        n=sum(map(int,str(n)))
        digital_root(n)
    return n 
```

#### 题7 Square Every Digit

Welcome. In this kata, you are asked to square every digit of a number.
For example, if we run 9119 through the function, 811181 will come out, because 92 is 81 and 12 is 1.

```
def square_digits(num):
    return int(''.join([str(n * n) for n in map(int, str(num))])) 
```

Note: The function accepts an integer and returns an integer

#### 题8 Find the odd int

Given an array, find the int that appears an odd number of times.
There will always be only one integer that appears an odd number of times.

```
from collections import Counter
def find_it(seq):
    timedict = Counter(seq)
    for i in timedict.keys():
        if timedict[i] % 2 != 0:
            return i 
```

#### 题9 Unique In Order

Implement the function unique_in_order which takes as argument a sequence and returns a list of items without any elements with the same value next to each other and preserving the original order of elements.
For example:
unique_in_order(‘AAAABBBCCDAABBB’) == [‘A’, ‘B’, ‘C’, ‘D’, ‘A’, ‘B’]
unique_in_order(‘ABBCcAD’) == [‘A’, ‘B’, ‘C’, ‘c’, ‘A’, ‘D’]
unique_in_order([1,2,2,3,3]) == [1,2,3]

```
from itertools import groupby
def unique_in_order(iterable):
    return [key for key, value in groupby(iterable)] 
```