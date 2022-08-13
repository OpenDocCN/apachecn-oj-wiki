<!--yml
category: codewars
date: 2022-08-13 11:50:34
-->

# Codewars-python每日练习（3）_创可不能贴的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_29060793/article/details/94394339?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-94394339.nonecase](https://blog.csdn.net/qq_29060793/article/details/94394339?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-94394339.nonecase)

# 1 Title Case

## Task

A string is considered to be in title case if each word in the string is either (a) capitalised (that is, only the first letter of the word is in upper case) or (b) considered to be an exception and put entirely into lower case unless it is the first word, which is always capitalised.

Write a function that will convert a string into title case, given an optional list of exceptions (minor words). The list of minor words will be given as a string with each word separated by a space. Your function should ignore the case of the minor words string – it should behave in the same way even if the case of the minor word string is changed.

## Arguments (Haskell)

First argument: space-delimited list of minor words that must always be lowercase except for the first word in the string.
Second argument: the original string to be converted.
###Arguments (Other languages)

First argument (required): the original string to be converted.
Second argument (optional): space-delimited list of minor words that must always be lowercase except for the first word in the string. The JavaScript/CoffeeScript tests will pass undefined when this argument is unused.

## Example

> title_case(‘a clash of KINGS’, ‘a an the of’) # should return: ‘A Clash of Kings’
> title_case(‘THE WIND IN THE WILLOWS’, ‘The In’) # should > return: ‘The Wind in the Willows’
> title_case(‘the quick brown fox’) # should return

* * *

```
def title_case(title, minor_words=''):
    title = title.capitalize().split()
    minor_words = minor_words.lower().split()
    return ' '.join([word if word in minor_words else word.capitalize() for word in title]) 
```

* * *

* * *

# 2 Does my number look big in this?

## Task

A Narcissistic Number is a number which is the sum of its own digits, each raised to the power of the number of digits in a given base. In this Kata, we will restrict ourselves to decimal (base 10).

## For example

take 153 (3 digits):

> 1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153

and 1634 (4 digits):

> 1^4 + 6^4 + 3^4 + 4^4 = 1 + 1296 + 81 + 256 = 1634

## The Challenge:

Your code must return true or false depending upon whether the given number is a Narcissistic number in base 10.

Error checking for text strings or other invalid inputs is not required, only valid integers will be passed into the function.

* * *

## 我的解决方法：

```
import numpy as np
def narcissistic( value ):
    val_str = str(value)
    dig_num = len(val_str)
    sum = 0
    for i in range(dig_num):
        sum = sum + np.power(int(val_str[i]),dig_num)
    return True if sum == value else False 
```

* * *

## 其他优秀解决方法：

```
def narcissistic(value):
    return value == sum(int(x) ** len(str(value)) for x in str(value)) 
```

* * *

* * *

# 3 IP Validation

## Task

Write an algorithm that will identify valid IPv4 addresses in dot-decimal format. IPs should be considered valid if they consist of four octets, with values between 0 and 255, inclusive.

Input to the function is guaranteed to be a single string.

## Examples

Valid inputs:

> 1.2.3.4
> 123.45.67.89

Invalid inputs:

> 1.2.3
> 1.2.3.4.5
> 123.456.78.90
> 123.045.067.089

Note that leading zeros (e.g. 01.02.03.04) are considered invalid.

* * *

```
def is_valid_IP(strng):
  lst = strng.split('.')
  passed = 0
  for sect in lst:
    if sect.isdigit():
      if sect[0] != '0':
        if 0 < int(sect) <= 255:
          passed += 1
  return passed == 4 
```