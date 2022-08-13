<!--yml
category: codewars
date: 2022-08-13 11:35:37
-->

# Codewars实战（三）_DilicelSten的博客-CSDN博客

> 来源：[https://blog.csdn.net/Totoro1745/article/details/87780804?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-87780804.142^v40^control,185^v2^control](https://blog.csdn.net/Totoro1745/article/details/87780804?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-87780804.142^v40^control,185^v2^control)

#### 题17 Weight for weight

It was decided to attribute a “weight” to numbers. The weight of a number will be from now on the sum of its digits.
For example 99 will have “weight” 18, 100 will have “weight” 1 so in the list 100 will come before 99\. Given a string with the weights of FFC members in normal order can you give this string ordered by “weights” of these numbers?
Example:
“56 65 74 100 99 68 86 180 90” ordered by numbers weights becomes: “100 180 90 56 65 74 68 86 99”

```
 def order_weight(strng):
    return ' '.join(sorted(sorted(strng.split(' ')),key = lambda x:sum(int(c) for c in x))) 
```

#### 题18 Build Tower

Build Tower by the following given argument:
number of floors (integer and always greater than 0).
Tower block is represented as *
Python: return a list;

```
def tower_builder(n):
    return [("*" * (i*2-1)).center(n*2-1) for i in range(1, n+1)] 
```

#### 题19 RGB To Hex Conversion

The rgb() method is incomplete. Complete the method so that passing in RGB decimal values will result in a hexadecimal representation being returned. The valid decimal values for RGB are 0 - 255\. Any (r,g,b) argument values that fall out of that range should be rounded to the closest valid value.
The following are examples of expected output values:
rgb(255, 255, 255) # returns FFFFFF
rgb(255, 255, 300) # returns FFFFFF
rgb(0,0,0) # returns 000000
rgb(148, 0, 211) # returns 9400D3

```
 def rgb(r, g, b):
    pre = lambda x: max(0, min(255, x)) 
    return '{:02x}{:02x}{:02x}'.format(pre(r),pre(g),pre(b)).upper() 
```

#### 题20 The Hashtag Generator

Here’s the deal:
It must start with a hashtag (#).
All words must have their first letter capitalized.
If the final result is longer than 140 chars it must return false.
If the input or the result is an empty string it must return false.

```
def generate_hashtag(s):
    if len(s) < 1 or len(s) > 140:
        return False
    else:
        result =[i[0].upper()+i[1:].lower() for i in s.split()]
        return '#' + ''.join(result)

def generate_hashtag(s):
    ans = '#'+ str(s.title().replace(' ',''))
    return s and not len(ans)>140 and ans or False 
```

#### 题21 Regex Password Validation

You need to write regex that will validate a password to make sure it meets the following criteria:
At least six characters long
contains a lowercase letter
contains an uppercase letter
contains a number
Valid passwords will only be alphanumeric characters.

```
 from re import compile, VERBOSE

regex = compile("""
^              # begin word
(?=.*?[a-z])   # at least one lowercase letter
(?=.*?[A-Z])   # at least one uppercase letter
(?=.*?[0-9])   # at least one number
[A-Za-z\d]     # only alphanumeric
{6,}           # at least 6 characters long
$              # end word
""", VERBOSE) 
```

#### 题22 Rot13

ROT13 is a simple letter substitution cipher that replaces a letter with the letter 13 letters after it in the alphabet. ROT13 is an example of the Caesar cipher.
Create a function that takes a string and returns the string ciphered with Rot13\. If there are numbers or special characters included in the string, they should be returned as they are. Only letters from the latin/english alphabet should be shifted, like in the original Rot13 “implementation”.

```
 import string
from codecs import encode as _dont_use_this_
from string import maketrans, lowercase, uppercase

def rot13(message):
    lower = maketrans(lowercase, lowercase[13:] + lowercase[:13])
    upper = maketrans(uppercase, uppercase[13:] + uppercase[:13])
    return message.translate(lower).translate(upper)

def rot13(message):
    return message.encode("rot13")

def rot13(message):
    return ''.join(chr((65 if c.isupper() else 97) + ((ord(c) - (65 if c.isupper() else 97)) + 13)%26) if c.isalpha() else c for c in message) 
```

#### 题23 Maximum subarray sum

The maximum sum subarray problem consists in finding the maximum sum of a contiguous subsequence in an array or list of integers:
maxSequence([-2, 1, -3, 4, -1, 2, 1, -5, 4])
should be 6: [4, -1, 2, 1]

```
 def maxSequence(arr):
    if len(arr)==0 or sum([x for x in arr if x > 0]) == 0:
        return 0
    else:
        max_ending_here=0
        max_so_far=0
        for each in arr:
            max_ending_here = max(0, max_ending_here + each)
            max_so_far = max(max_so_far, max_ending_here)
        return max_so_far

def maxSequence(arr):
    max,curr=0,0
    for x in arr:
        curr+=x
        if curr<0:curr=0
        if curr>max:max=curr
    return max 
```

#### 题24 Twice linear

Consider a sequence u where u is defined as follows:
The number u(0) = 1 is the first one in u.
For each x in u, then y = 2 * x + 1 and z = 3 * x + 1 must be in u too.
There are no other numbers in u.
Ex: u = [1, 3, 4, 7, 9, 10, 13, 15, 19, 21, 22, 27, …]
1 gives 3 and 4, then 3 gives 7 and 10, 4 gives 9 and 13, then 7 gives 15 and 22 and so on…
Given parameter n the function dbl_linear (or dblLinear…) returns the element u(n) of the ordered (with <) sequence u.
Example:
dbl_linear(10) should return 22

```
 def dbl_linear(n):
  num_list = [1]
  for i in num_list:
    num_list.append((i * 2) + 1)
    num_list.append((i * 3) + 1)
    if len(num_list) > n *10:
      break
  return sorted(list(set(num_list)))[n]

from collections import deque

def dbl_linear(n):
    h = 1; cnt = 0; q2, q3 = deque([]), deque([])
    while True:
        if (cnt >= n):
            return h
        q2.append(2 * h + 1)
        q3.append(3 * h + 1)
        h = min(q2[0], q3[0])
        if h == q2[0]: h = q2.popleft()
        if h == q3[0]: h = q3.popleft()
        cnt += 1 
```