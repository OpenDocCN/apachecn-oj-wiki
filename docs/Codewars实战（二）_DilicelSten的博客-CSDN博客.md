<!--yml
category: codewars
date: 2022-08-13 11:28:06
-->

# Codewars实战（二）_DilicelSten的博客-CSDN博客

> 来源：[https://blog.csdn.net/Totoro1745/article/details/87701681?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-87701681.142^v40^control,185^v2^control](https://blog.csdn.net/Totoro1745/article/details/87701681?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-87701681.142^v40^control,185^v2^control)

#### 题10 Regex validate PIN code

ATM machines allow 4 or 6 digit PIN codes and PIN codes cannot contain anything but exactly 4 digits or exactly 6 digits.
validate_pin(“1234”) == True
validate_pin(“12345”) == False
validate_pin(“a234”) == False

```
def validate_pin(pin):
    if len(pin) == 4 or len(pin) == 6:
        return pin.isdigit()
    else:
        return False
def validate_pin(pin):
    return len(pin) in (4, 6) and pin.isdigit() 
```

#### 题11 Equal Sides Of An Array

You are going to be given an array of integers. Your job is to take that array and find an index N where the sum of the integers to the left of N is equal to the sum of the integers to the right of N. If there is no index that would make this happen, return -1.

```
def find_even_index(arr):
    for i in range(len(arr)):
        if sum(arr[:i]) == sum(arr[i+1:]):
            return i
        else:
            pass
    return -1 
```

#### 题12 Simple Pig Latin

Move the first letter of each word to the end of it, then add “ay” to the end of the word. Leave punctuation marks untouched.
pig_it(‘Pig latin is cool’) # igPay atinlay siay oolcay
pig_it(‘Hello world !’) # elloHay orldway !

```
def pig_it(text):
    result = []
    wordlist = text.split()
    for each in wordlist:
        if each.isalpha():
            result.append(each[1:] + each[0] + 'ay')
        else:
            result.append(each)
    return ' '.join(result)

def pig_it(text):
    lst = text.split()
    return ' '.join( [word[1:] + word[:1] + 'ay' if word.isalpha() else word for word in lst]) 
```

#### 题13 Calculating with Functions

This time we want to write calculations using functions and get the results

```
 import math
def zero(f = None):
    return 0 if not f else f(0)
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
def divided_by(y): return lambda  x: math.floor(x/y) 
```

#### 题14 Create Phone Number

Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.
create_phone_number([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]) # => returns “(123) 456-7890”

```
 def create_phone_number(n):
    n = ''.join(str(i) for i in n)
    return '({}) {}-{}'.format(n[:3], n[3:6], n[6:])

def create_phone_number(n):
  return "({}{}{}) {}{}{}-{}{}{}{}".format(*n) 
```

#### 题15 Valid Parentheses

Write a function called that takes a string of parentheses, and determines if the order of the parentheses is valid. The function should return true if the string is valid, and false if it’s invalid.
Examples
“()” => true
“)(()))” => false
“(” => false
“(())((()())())” => true

```
 def valid_parentheses(string):
    cnt = 0
    for char in string:
        if char == '(': cnt += 1
        if char == ')': cnt -= 1
        if cnt < 0: return False
    return True if cnt == 0 else False 
```

#### 题16 Find The Parity Outlier

You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns this “outlier” N.
Examples
[2, 4, 0, 100, 4, 11, 2602, 36]
Should return: 11 (the only odd number)
[160, 3, 1719, 19, 11, 13, -21]
Should return: 160 (the only even number)

```
def find_outlier(integers):
    even = [i for i in integers if i % 2 == 0]
    odd = [i for i in integers if i % 2 != 0]
    if len(even) < len(odd):
        return even[0]
    else:
        return odd[0] 
```