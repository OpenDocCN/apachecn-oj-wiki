<!--yml
category: codewars
date: 2022-08-13 11:39:43
-->

# codewars【5】_幻梦鸵鸟的博客-CSDN博客

> 来源：[https://blog.csdn.net/i897355249/article/details/99411877?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-3-99411877-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/i897355249/article/details/99411877?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-3-99411877-null-null.142^v40^control,185^v2^control&utm_term=codewars)

**1.Not very secure**
In this example you have to validate if a user input string is alphanumeric.
The string has the following conditions to be alphanumeric:

At least one character ("" is not valid)
Allowed characters are uppercase / lowercase latin letters and digits from 0 to 9

My solution:

```
def alphanumeric(string):
    if string!="":
        for i in string:
            if i.isalpha()==False and i.isdigit()==False:
                return False
        return True
    return False
    pass 
```

Clever solution NO.1:

```
def alphanumeric(string):
    return string.isalnum() 
```

*Python自带的isalnum()方法，可以检测字符串是否由字母和数字组成。*
**2.int32 to IPv4**
Take the following IPv4 address: 128.32.10.1
This address has 4 octets where each octet is a single byte (or 8 bits).

1st octet 128 has the binary representation: 10000000
2nd octet 32 has the binary representation: 00100000
3rd octet 10 has the binary representation: 00001010
4th octet 1 has the binary representation: 00000001

So 128.32.10.1 == 10000000.00100000.00001010.00000001
Because the above IP address has 32 bits, we can represent it as the unsigned 32 bit number: 2149583361
Complete the function that takes an unsigned 32 bit number and returns a string representation of its IPv4 address.
Examples

```
2149583361 ==> "128.32.10.1"
32         ==> "0.0.0.32"
0          ==> "0.0.0.0" 
```

My solution：

```
def int32_to_ip(int32):
    # your code here
    a=bin(int32)
    b=a[2:len(a)].zfill(32)
    return "{}.{}.{}.{}".format(int(b[0:8],2),int(b[8:16],2),int(b[16:24],2),int(b[24:32],2)) 
```

**3.Greed is Good**
Greed is a dice game played with five six-sided dice. Your mission, should you choose to accept it, is to score a throw according to these rules. You will always be given an array with five six-sided dice values.

```
Three 1's => 1000 points
 Three 6's =>  600 points
 Three 5's =>  500 points
 Three 4's =>  400 points
 Three 3's =>  300 points
 Three 2's =>  200 points
 One   1   =>  100 points
 One   5   =>   50 point 
```

A single die can only be counted once in each roll. For example, a “5” can only count as part of a triplet (contributing to the 500 points) or as a single 50 points, but not both in the same roll.
Example scoring

```
Throw       Score
 ---------   ------------------
 5 1 3 4 1   50 + 2 * 100 = 250
 1 1 1 3 1   1000 + 100 = 1100
 2 4 4 5 4   400 + 50 = 450 
```

My solution:

```
def score(dice):
    # your code here
    num=0
    if dice.count(1)<3:
        num+=100*(dice.count(1))
    if dice.count(1)>=3:
        num+=1000+100*(dice.count(1)-3)
    for i in range(2,5):
        if dice.count(i)>=3:
            num+=(100*i)
    if dice.count(6)==3:
        num+=600
    if dice.count(5)<3:
        num+=50*dice.count(5)
    if dice.count(5)>=3:
        num+=500+50*(dice.count(5)-3)
    return num 
```

Clever solution NO.1:

```
def score(dice): 
  sum = 0
  counter = [0,0,0,0,0,0]
  points = [1000, 200, 300, 400, 500, 600]
  extra = [100,0,0,0,50,0]
  for die in dice: 
    counter[die-1] += 1

  for (i, count) in enumerate(counter):
    sum += (points[i] if count >= 3 else 0) + extra[i] * (count%3)

  return sum 
```