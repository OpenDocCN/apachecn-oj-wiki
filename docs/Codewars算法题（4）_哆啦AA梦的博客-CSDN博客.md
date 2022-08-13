<!--yml
category: codewars
date: 2022-08-13 11:49:01
-->

# Codewars算法题（4）_哆啦AA梦的博客-CSDN博客

> 来源：[https://blog.csdn.net/y1535766478/article/details/76040146?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-76040146.nonecase](https://blog.csdn.net/y1535766478/article/details/76040146?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-76040146.nonecase)

第七题：（3和5的倍数）

问题： 

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9\. The sum of these multiples is 23.Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in.

代码实现：

```
**def** solution(number):
  s=n=0
  **for** i **in** range(1,number):
  **if** i%3==0:
  s=s+i
        **elif** i%5==0 **and** i%3!=0:
  n=n+i
    **return** s+n
```

这个方法简直简单粗暴到极点~~~~

评分较高代码：

(1)

```
**def** **solution**(number):
  **return** sum([n **for** n **in** range(1,number) **if** n%3==0 **or** n%5==0])
```

本质上就是写到一起了，不过看起来更加优雅

(2)

```
**def** **solution**(number):
  threes = range(3, number, 3)
    fives = range(5, number, 5)
    **return** sum(list(set(threes + fives)))
```

不过我觉得（2）方法也是挺好的，巧妙的运用了set()方法

第八题：（拆分字符串）

问题：Complete the solution so that it splits the string into pairs of two characters. If the string contains an odd number of characters then it should replace the missing second character of the final pair with an underscore ('_').

Examples:

solution('abc')

solution('abcdef')

```
**def** **solution**(s):
  **return** [(s + "_")[i:i + 2] **for** i **in** range(0, len(s), 2)]
```

（2）

```
**def** **solution**(s):
  **return** [s[x:x+2] **if** x < len(s) - 1 **else** s[-1] + "_" **for** x **in** range(0, len(s), 2)]
```

两者都用了列表推倒式——轻量级循环，（1）中无论s是什么情况都会在s后面增加_，因为当len(s)是偶数时，不会对_进行切片的，简直完美。

第九题：（一个单词中有5个或更多字母时，则单词中逐个字母反写）

问题：

Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed (Just like the name of this Kata). Strings passed in will consist of only letters and spaces. Spaces will be included only when more than one word is present. 

Examples: 

`spinWords( "Hey fellow warriors" )` => returns "Hey wollef sroirraw" 
`spinWords( "This is a test")` => returns "This is a test" 
`spinWords( "This is another test" )`=> returns "This is rehtona test"

实现代码：

```
**def** **spin_words**(sentence):
  result=[]
    s=sentence.split()#对字符串进行分割
  **for** i **in** s:
  **if** len(i)>=5:
  i=i[::-1]
        result.append(i)
    **return** ' '.join(result)
```

评分较高代码：

（1）

```
**def** **spin_words**(sentence):
  **return** " ".join([x[::-1] **if** len(x) >= 5 **else** x **for** x **in** sentence.split(" ")])
```

列表循环使得代码更加优雅

（2）

```
**def** **spin_words**(sentence):
  words = [word **for** word **in** sentence.split(" ")]
    words = [word **if** len(word) < 5 **else** word[::-1] **for** word **in** words]
    **return** " ".join(words)
```

第十题：判断是否为三角形

问题：

Implement a method that accepts 3 integer values a, b, c. The method should return true if a triangle can be built with the sides of given length and false in any other case.

代码实现：

```
**def** **is_triangle**(a, b, c):
  a, b, c = sorted([a, b, c])
    **return** a + b > c
```

第十一题：（删除元素出现次数超过n次的情况）

问题：

例如：

【1,1,2,2,3,3,3,3】3       应返回【1,1,2,2,3,3,3】

代码实现：

```
**def** **find_next_square**(sq):
  # Return the next square if sq is a square, -1 otherwise
  s=[i*i **for** i **in** range(0,1000000)]
    **if** sq **in** s:
  **return** s[s.index(sq)+1]
    **else**:
  **return** -1
```

自己当时好像脑残~~~~

评分较高代码：

（1）

```
**def** **find_next_square**(sq):
  root = sq ** 0.5
  **if** root.is_integer():
  **return** (root + 1) ** 2
  **return** -1
```

```
（2）
```

 ```
def **find_next_square**(sq):
```

```
  x = sq ** 0.5
  **return** -1 **if** x % 1 **else** (x + 1) ** 2
```

第十二题：（寻找丢失的字母）

问题：

Write a method that takes an array of consecutive (increasing) letters as input and that returns the missing letter in the array.

You will always get an valid array. And it will be always exactly one letter be missing. The length of the array will always be at least 2.
The array will always contain letters in only one case.

Example:

```
['a','b','c','d','f'] -> 'e'
['O','Q','R','S'] -> 'P'
```

评分较高代码：

（1）

```
**def** **find_missing_letter**(chars):
  n = 0
  **while** ord(chars[n]) == ord(chars[n+1]) - 1:
  n += 1
  **return** chr(1+ord(chars[n]))
```

在这里需要简单介绍一下ord()和chr(),根据字母所对应的ASCII值，我们科得到chr(65)='A';ord('a')=97

(2)

```
**def** **find_missing_letter**(c):
  **return** next(chr(ord(c[i])+1) **for** i **in** range(len(c)-1) **if** ord(c[i])+1 != ord(c[i+1]))
```

next()函数必须接收一个可迭代对象参数，每次调用的时候，返回可迭代对象的下一个元素。如果所有元素均已经返回过，则抛出 异常。虽然（2）代码较为优雅，但本人还是比较倾向于（1）代码的，因为其可读性比较好。 

(3)

```
**def** **find_missing_letter**(chars):
  s = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
  match = False
  count = 0;
    **for** letter **in** s:
  **if** letter == chars[count]:
  match = True
  count = count +1
  **elif** match == True:
  **return** letter
```

第十三题：(建房子)

问题：Your task is to construct a building which will be a pile of n cubes. The cube at the bottom will have a volume of n^3, the cube above will have volume of (n-1)^3 and so on until the top which will have a volume of 1^3.

You are given the total volume m of the building. Being given m can you find the number n of cubes you will have to build?

The parameter of the function findNb `(find_nb, find-nb, findNb)`will be an integer m and you have to return the integer n such as n^3 + (n-1)^3 + ... + 1^3 = m if such a n exists or -1 if there is no such n.

## Examples:

findNb(1071225) --> 45

findNb(91716553919377) --> -1 

问题陈述：

建造一个建筑物，现在知道建筑物的体积是M，最下面一层的体积是N的3次方，第二层的体积是N-1的的三次方，

依次类推，最顶层的体积是1的三次方；也就是M=N^3+(N-1)^3+....+1^3是否存在，若存在则返回N，否则返回-1

代码实现：

（1）

```
**def** **find_nb**(m):
  n=1
  **while**(m>0):
  m=m-n*n*n
        n=n+1
  **return** n-1 **if** m==0 **else** -1
```

主要是一个逆推的过程，从顶层开始，依次减去每层的体积，直到M=0为止（返回N），若M不能等于0（M<0）则返回-1

得分较高代码：

```
**def** **find_nb**(m):
  n = 1
  volume = 0
  **while** volume < m:
  volume += n**3
  **if** volume == m:
  **return** n
        n += 1
  **return** -1
```

第十四题：(删除字符串中的元音)

问题：去掉所给字符串中的元音字母

代码实现：

```
**def** **disemvowel**(string):
  out=[]
    l=list(string)
    s=['a','e','i','o','u','A','E','I','O','U']
    **for** i **in** string:
  **if** i **not in** s:
  out.append(i)
    **return** ''.join(out)
```

评分较高代码：

（1）

```
**def** **disemvowel**(s):
  **return** s.translate(None, "aeiouAEIOU")
```

看到这一段代码的时候，又刷新了我对python的认识~~~~~

第一：现在简单介绍一下translate（）函数：进行字符串的删除，第一个参数是字符串转换规则表，

第二个参数是要删除的字符

第二：还有一个函数和translate（）相关，那就是maketrans（）函数，作用是设置字符串转化规则表。

具体介绍看[帖子](http://www.jb51.net/article/15701.htm)

（2）

```
**def** **disemvowel**(string):
  **return** "".join(c **for** c **in** string **if** c.lower() **not in** "aeiou")
```

第十五题：计算重复次

问题：Write a function that will return the count of distinct case-insensitive alphabetic characters and numeric digits that occur more than once

in the input string. The input string can be assumed to contain only alphabets (both uppercase and lowercase) and numeric digits.

代码实现：

```
**def** **duplicate_count**(text):
  s = text.lower()
    result=[]
    l = list(s)
    **for** i **in** s:
  **if** s.count(i) >= 2 **and** i **not in** result:
  result.append(i)
    **return** len(result)
```

得分较高代码：

```
**def** **duplicate_count**(s):
  **return** len([c **for** c **in** set(s.lower()) **if** s.lower().count(c)>1])
```

该代码主要用到了列表循环和set()函数，用set()的目的是把字符串中的字母唯一化，避免重复处理重复的字母

第十六题：

问题：

Write a function that takes an (unsigned) integer as input, and returns the number of bits that are equal to one in the binary representation of that number.

Example: The binary representation of `1234` is `10011010010`, so the function should return `5` in this case

其实就是将一个十进制转化为二进制，返回二进制中1的个数

实现代码：

```
**def** **countBits**(n):
  **return** bin(n).count("1")
```

这里巧妙的运用了bin()函数，作用是将十进制转化为二进制（开头会有0b,但不影响本题）

普及一下：将十进制转化为八进制，使用函数：oct()

将十进制转化为十六进制，使用函数：hex()

第十七题：

问题：

Given an array of one's and zero's convert the equivalent binary value to an integer.

Eg: [0, 0, 0, 1] is treated as 0001 which is the binary representation of 1

      [0,1,1,1]is treated as 0111 which is the binary representation of 7

实现代码：

```
**def** **binary_array_to_number**(arr):
  sum=0
  **for** i **in** range(1,(len(arr)+1)):
  a=arr[-i]*2**(i-1)
        sum=sum+a
    **return** sum
```

评分较高代码：

```
（1）
```

 ```
**def** **binary_array_to_number**(arr):
  **return** int("".join(map(str, arr)), 2)
```

其中的2的意思是二进制，举个栗子：int(11,2)=3

(2)

```
**def** **binary_array_to_number**(arr):
  s = 0
  **for** digit **in** arr:
  s = s * 2 + digit
    **return** s
```

(3)

```
**def** **binary_array_to_number**(arr):
  **return** sum(digit * 2**i **for** i, digit **in** enumerate(reversed(arr)))
```

(4)

```
**from** functools **import** reduce
**def** **binary_array_to_number**(a):
  **return** reduce(**lambda** t,b:t*2+b,a)
```

这个方法的主要亮点在于使用了reduce()函数，会对数据集中的数据依次进行操作，本方法实现了累加的效果。

201707252128 持续更新~~~