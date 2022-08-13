<!--yml
category: codewars
date: 2022-08-13 11:51:37
-->

# Codewars刷题（水仙花数判断）_avicarima的博客-CSDN博客

> 来源：[https://blog.csdn.net/avicarima/article/details/83913216?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-83913216.nonecase](https://blog.csdn.net/avicarima/article/details/83913216?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-83913216.nonecase)

# Instructions

A Narcissistic Number is a number which is the sum of its own digits, each raised to the power of the number of digits in a given base. In this Kata, we will restrict ourselves to decimal (base 10).

For example, take 153 (3 digits):
1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153
and 1634 (4 digits):
1^4 + 6^4 + 3^4 + 4^4 = 1 + 1296 + 81 + 256 = 1634

# The Challenge

Your code must return true or false depending upon whether the given number is a Narcissistic number in base 10.
Error checking for text strings or other invalid inputs is not required, only valid integers will be passed into the function.

# 中文说明

该题目要实现的程序为编写一个函数判断一个十进制整数是否为自幂数。自幂数是指一个 n 位数，它的每个位上的数字的 n 次幂之和等于它本身。

例：
以十进制153为例，此时n为3，有1^3 + 5^3 + 3^3 = 153，153即是3位的自幂数，也称水仙花数（Narcissistic number）；
以十进制1634为例，此时n为4，有1^4 + 6^4 + 3^4 + 4^4 = 1634，1634即是4位的自幂数，也称为四叶玫瑰数。

该题目不要求检查输入内容的合法性，仅建立在正确输入一位十进制整数的情况下。

# The cleverest code(From Codewars)

```
def narcissistic(value):
    return value == sum(int(x) ** len(str(value)) for x in str(value))
```

# My code（Tested on my own PC and Codewars web）

```
def narcissistic(value):
    number_of_digits = len(str(value))
    sum_result = 0
    for digit in str(value):
        sum_result += int(digit)**number_of_digits
    if sum_result == value:
        return True
    else:
        return False

if __name__ == '__main__':
    int_input = int(input("Please input a int number:"))
    print(int_input, narcissistic(int_input))
```

# Test Cases

```
test.describe("Narcissistic function")
test.it("Should find these small numbers narcissistic...")
test.assert_equals(narcissistic(1), True, '1 is narcissistic')
test.assert_equals(narcissistic(5), True, '5 is narcissistic')
test.assert_equals(narcissistic(7), True, '7 is narcissistic')

test.it("Should find these larger numbers narcissistic...")
test.assert_equals(narcissistic(153), True, '153 is narcissistic')
test.assert_equals(narcissistic(370), True, '370 is narcissistic')
test.assert_equals(narcissistic(371), True, '371 is narcissistic')
test.assert_equals(narcissistic(1634), True, '1634 is narcissistic')

test.it("Should not find these numbers narcissistic...")
from random import randint
for a in range(0,10):
    num = randint(5,9) * 60000 + randint(1,99)
    test.assert_equals(narcissistic(num), False, '%d is not narcissistic' % num)

bignums = [8208, 9474, 54748, 92727, 93084, 548834, 1741725, 4210818, 9800817, 9926315, 24678050, 24678051]

test.it('Should find some of these narcissistic...')
for b in bignums:
    if randint(0,10) > 5:
        test.assert_equals(narcissistic(b), True, '%d is narcissistic' % b)
    else:
        num = randint(5,9) * 900000 + randint(1,99)
        test.assert_equals(narcissistic(num), False, '%d is not narcissistic' % num)
```

# 附注（自幂数相关）

自幂数是指一个 n 位数，它的每个位上的数字的 n 次幂之和等于它本身。
n为1时，自幂数称为独身数。显然，0,1,2,3，4,5,6,7,8,9都是自幂数。
n为2时，没有自幂数；
n为3时，自幂数称为水仙花数，有4个：153，370，371，407；
n为4时，自幂数称为四叶玫瑰数，共有3个：1634，8208，9474；
n为5时，自幂数称为五角星数，共有3个：54748，92727，93084；
n为6时，自幂数称为六合数， 只有1个：548834；
n为7时，自幂数称为北斗七星数， 共有4个：1741725，4210818，9800817，9926315；
n为8时，自幂数称为八仙数， 共有3个：24678050，24678051，88593477；
n为9时，自幂数称为九九重阳数，共有4个：146511208，472335975，534494836，912985153；
n为10时，自幂数称为十全十美数，只有1个：4679307774。