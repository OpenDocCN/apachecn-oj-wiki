<!--yml
category: codewars
date: 2022-08-13 11:43:37
-->

# 入坑codewars第十天-Product of consecutive Fib numbers、longest_palindrome_渣渣琪的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_37341950/article/details/84871597?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-84871597.nonecase](https://blog.csdn.net/sinat_37341950/article/details/84871597?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-84871597.nonecase)

题目：

The Fibonacci numbers are the numbers in the following integer sequence (Fn):

> 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, ...

such as

> F(n) = F(n-1) + F(n-2) with F(0) = 0 and F(1) = 1.

Given a number, say prod (for product), we search two Fibonacci numbers F(n) and F(n+1) verifying

> F(n) * F(n+1) = prod.

Your function productFib takes an integer (prod) and returns an array:

```
[F(n), F(n+1), true] or {F(n), F(n+1), 1} or (F(n), F(n+1), True) 
```

depending on the language if F(n) * F(n+1) = prod.

If you don't find two consecutive F(m) verifying `F(m) * F(m+1) = prod`you will return

```
[F(m), F(m+1), false] or {F(n), F(n+1), 0} or (F(n), F(n+1), False) 
```

F(m) being the smallest one such as `F(m) * F(m+1) > prod`.

# Examples

```
productFib(714) # should return [21, 34, true], 
                # since F(8) = 21, F(9) = 34 and 714 = 21 * 34

productFib(800) # should return [34, 55, false], 
                # since F(8) = 21, F(9) = 34, F(10) = 55 and 21 * 34 < 800 < 34 * 55 
```

**Notes:** Not useful here but we can tell how to choose the number n up to which to go: we can use the "golden ratio" phi which is `(1 + sqrt(5))/2` knowing that F(n) is asymptotic to: `phi^n / sqrt(5)`. That gives a possible upper bound to n.

You can see examples in "Example test".

### References

[http://en.wikipedia.org/wiki/Fibonacci_number](http://en.wikipedia.org/wiki/Fibonacci_number)

[http://oeis.org/A000045](http://oeis.org/A000045)

题意：

```
题意就是输入一个数，找出斐波那契序列中连续两个数相乘等于此数，则输出这两个数和True；否则输出这刚好大于这个数的两个数的乘积和False
```

解题思路：

```
思路：
我的思路是先循环遍历；从0、1、1、2、3、5……两两相乘，直到等于输入的数，则输出[两个数，True],否则输出刚好大于这个数乘积的两个数[两个数，False] 
```

代码：

```
def productFib(prod):
    f=[]
    f.append(0)
    f.append(1)
    list1=[]
    for i in range(2,prod):
        f.append(f[i-1]+f[i-2])
        if f[i]*f[i-1] == prod:
            list1.append(f[i-1])
            list1.append(f[i])
            list1.append(True)
            return list1
        if f[i]*f[i-1] > prod:
            list1.append(f[i-1])
            list1.append(f[i])
            list1.append(False)
            return list1
    return None
```

我的思路很简单，接下来看看大佬的精简代码：

```
def productFib(prod):
  a, b = 0, 1
  while prod > a * b:
    a, b = b, a + b
  return [a, b, prod == a * b]
```

相当精炼：真的棒！只用了两个变量就解决了这个问题。

题目二：

这道题没写出来，写了可以但是timeout

### Longest Palindrome

Find the length of the longest substring in the given string `s` that is the same in reverse.

As an example, if the input was “I like racecars that go fast”, the substring (`racecar`) length would be `7`.

If the length of the input string is `0`, the return value must be `0`.

### Example:

```
"a" -> 1 
"aab" -> 2  
"abcde" -> 1
"zzbaabcd" -> 4
"" -> 0
```

题意：

```
题意就是找到一串连续字符串左边和右边对称并且要是最长的；
如："zzbaabcd" -> 4 其中baab就是这个字符串 
```

代码如下：

```
我的解法很简单就是把字符串每个子串部分放在一个列表中，然后把字符串颠倒，将其子串放在一个列表中，然后匹配，计算最长匹配值返回。
然而超时了： 
```

```
def longest_palindrome(s):
    #s[::-1]颠倒字符串
    a=s
    b=s[::-1]
    #print(b[-1])
    length=len(s)
    ls=[]
    ls1=[]
    maxlength=0
    for i in range(0,length):
        for j in range(i+1,length+1):
            c = a[i:j]
            ls.append(c)
    #print(ls)
    for i in range(0,length):
        for j in range(i+1,length+1):
            d = b[i:j]
            ls1.append(d)
    #print(ls1)
    for j in ls:
        if j in ls1:
            num=len(j)
            maxlength=max(num,maxlength)
    return maxlength
```

```
#AC代码：大神精简代码
def longest_palindrome(s):
    for i in range(len(s), 0, -1):
        for j in range(len(s)-i+1):
            #print(i,j)
            sub = s[j:j+i]
            #print(sub)
            if sub == sub[::-1]:
                return i
    return 0
#print(longest_palindrome("abcdefghba"), 1)
```

加了两个print，理解此代码的输出过程：我大概理解了是固定长度，变区间；比如一开始i就代表字符串长度10，然后区间就只有一个0-10；接下来i减少1，则区间可以是0-9，1-10；i=8时，就有三个区间：0-8、1-9、2-10；以此类推……

```
10 0
abcdefghba
9 0
abcdefghb
9 1
bcdefghba
8 0
abcdefgh
8 1
bcdefghb
8 2
cdefghba
7 0
abcdefg
7 1
bcdefgh
7 2
cdefghb
7 3
defghba
6 0
abcdef
6 1
bcdefg
6 2
cdefgh
6 3
defghb
6 4
efghba
5 0
abcde
5 1
bcdef
5 2
cdefg
5 3
defgh
5 4
efghb
5 5
fghba
4 0
abcd
4 1
bcde
4 2
cdef
4 3
defg
4 4
efgh
4 5
fghb
4 6
ghba
3 0
abc
3 1
bcd
3 2
cde
3 3
def
3 4
efg
3 5
fgh
3 6
ghb
3 7
hba
2 0
ab
2 1
bc
2 2
cd
2 3
de
2 4
ef
2 5
fg
2 6
gh
2 7
hb
2 8
ba
1 0
a
1 1
```