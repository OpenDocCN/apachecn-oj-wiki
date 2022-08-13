<!--yml
category: codewars
date: 2022-08-13 11:37:54
-->

# Codewars笔记_EverybodyDies的博客-CSDN博客

> 来源：[https://blog.csdn.net/everybodydies/article/details/89333943?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-89333943.142^v40^control,185^v2^control](https://blog.csdn.net/everybodydies/article/details/89333943?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-89333943.142^v40^control,185^v2^control)

# Codewars笔记

## 1.Replace With Alphabet Position

Introduction
Welcome. In this kata you are required to, given a string, replace every letter with its position in the alphabet. If anything in the text isn’t a letter, ignore it and don’t return it. a being 1, b being 2, etc. As an example:

`"a" = 1, "b" = 2`
,etc

Example

```
alphabet_position("The sunset sets at twelve o' clock.") 
```

should return`"20 8 5 19 21 14 19 5 20 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11"` (as a string)

## My Submit

```
def alphabet_position(text):
    letter = []
    for i in text:
        a = ord(i)
        if a >= 65 and a <= 90:
            a -= 64
        elif a >= 97 and a <= 122:
            a -= 96
        else:
            continue
        letter.append(str(a))
    return " ".join(letter) 
```

## 2\. Is a number prime?

Define a function isPrime/is_prime() that takes one integer argument and returns true/True or false/False depending on if the integer is a prime.

Per Wikipedia, a prime number (or a prime) is a natural number greater than 1 that has no positive divisors other than 1 and itself.

Example

```
bool isPrime(5) = return true 
```

Assumptions
You can assume you will be given an integer input.
You can not assume that the integer will be only positive. You may be given negative numbers as well (or 0).

## My Submit

```
def is_prime(num):
        if num <= 1:
            return False
        elif num == 2:
            return True
        else:    
            c = 2
            while c < num:
                if num % c == 0:
                    return False
                    break
                c = c+1    
            else:
                return True 
```