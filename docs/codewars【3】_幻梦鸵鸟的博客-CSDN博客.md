<!--yml
category: codewars
date: 2022-08-13 11:47:22
-->

# codewars【3】_幻梦鸵鸟的博客-CSDN博客

> 来源：[https://blog.csdn.net/i897355249/article/details/99173492?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-99173492.nonecase](https://blog.csdn.net/i897355249/article/details/99173492?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-99173492.nonecase)

**1.Count the smiley faces!**
Given an array (arr) as an argument complete the function countSmileys that should return the total number of smiling faces.

Rules for a smiling face:

-Each smiley face must contain a valid pair of eyes.
Eyes can be marked as `:`or`;`

-A smiley face can have a nose but it does not have to.
Valid characters for a nose are `-` or `~`

-Every smiling face must have a smiling mouth that should be marked with either `)` or `D`.

No additional characters are allowed except for those mentioned.

Valid smiley face examples:

```
:) :D ;-D :~) 
```

Invalid smiley faces:

```
;( :> :} :] 
```

My solution:

```
def count_smileys(arr):
    count=0
    for each in arr:
        if len(each)==3:
            if ')' in each or 'D' in each:
                if '-' in each or '~' in each:
                    count=count+1
        if len(each)==2:
            if ')' in each or 'D' in each:
                count=count+1
    return count 
```

Clever solution NO.1:

```
from re import findall
def count_smileys(arr):
    return len(list(findall(r"[:;][-~]?[)D]", " ".join(arr)))) 
```

Clever solution NO.2:

```
def count_smileys(arr):
    eyes = [":", ";"]
    noses = ["", "-", "~"]
    mouths = [")", "D"]
    count = 0
    for eye in eyes:
        for nose in noses:
            for mouth in mouths:
                face = eye + nose + mouth
                count += arr.count(face)
    return count 
```

**2.Find the missing letter**
Write a method that takes an array of consecutive (increasing) letters as input and that returns the missing letter in the array.
You will always get an valid array. And it will be always exactly one letter be missing. The length of the array will always be at least 2.
The array will always contain letters in only one case.
Example:

```
['a','b','c','d','f'] -> 'e'
['O','Q','R','S'] -> 'P' 
```

My solution:

```
def find_missing_letter(chars):
    for i in range(len(chars)):
        if ord(chars[i])+1!=ord(chars[i+1]):
            return chr(ord(chars[i])+1) 
```

Clever solution NO.1:

```
def find_missing_letter(chars):
    n = 0
    while ord(chars[n]) == ord(chars[n+1]) - 1:
        n += 1
    return chr(1+ord(chars[n])) 
```

*ord()函数将字符转化为asc码
chr()函数将asc码转化为字符*

**3.Your order,please**
Your task is to sort a given string. Each word in the string will contain a single number. This number is the position the word should have in the result.
Note: Numbers can be from 1 to 9\. So 1 will be the first word (not 0).
If the input string is empty, return an empty string.
The words in the input String will only contain valid consecutive numbers.
Examples

```
"is2 Thi1s T4est 3a"  -->  "Thi1s is2 3a T4est"
"4of Fo1r pe6ople g3ood th5e the2"  -->  "Fo1r the2 g3ood 4of th5e pe6ople"
""  -->  "" 
```

My solution:

```
import re
def order(sentence):
  # code here
  if sentence=="":
      return ""
  else:
      s=sentence.split()
      length=len(s)
      a=[[] for i in range(length)]
      for i in s:
          num=[int(x) for x in re.findall('(\d+)',i)]
          a[num[0]-1]=i
      b=' '.join(a)
      return b 
```

Clever solution NO.1:

```
def order(sentence):
    return " ".join(sorted(sentence.split(), key=lambda x: int(filter(str.isdigit, x)))) 
```

解题中的若干知识点：
(1)初始化长度为n的空列表：
`[[] for x in range(n)]`
(2)re.findall正则
(3)sorted语法
`sorted(iterable, key=None, reverse=False)`
参数说明：
iterable – 可迭代对象
key – 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序
reverse – 排序规则，reverse = True 降序 ， reverse = False 升序（默认）
返回值为返回重新排序的列表。

**4.CamelCase Method**
All words must have their first letter capitalized without spaces.
For instance:

```
camelcase("hello case") => HelloCase
camelcase("camel case word") => CamelCaseWord 
```

My solution:

```
def camel_case(string):
    #your code here
    l=list(string)
    length=len(l)
    if string=="":
        return ""
    else:
        if l[0]!=" ":
            l[0]=chr(ord(l[0])-32)
            for i in range(length-1):
                if l[i]==" " :
                    l[i+1]=chr(ord(l[i+1])-32)
            for i in range(l.count(' ')):
                l.remove(' ')
            s=''.join(l)
            return s
        if l[0]==" ":
            for i in range(length-1):
                if l[i]==" " :
                    l[i+1]=chr(ord(l[i+1])-32)
            for i in range(l.count(' ')):
                l.remove(' ')
            s=''.join(l)
            return s 
```

Clever solution NO.1:

```
def camel_case(string):
    return string.title().replace(" ", "") 
```

*此题看出基础功的重要，python自带的函数title()能够极为简单的解决此题。*

```
str.title() 
```

*返回"标题化"的字符串,就是说所有单词的首字母都转化为大写。
请注意，非字母后的第一个字母将转换为大写字母：*

```
txt = "hello b2b2b2 and 3g3g3g"
x = txt.title()
print(x) 
```

**4.Moving Zeros To The End**
Write an algorithm that takes an array and moves all of the zeros to the end, preserving the order of the other elements.

```
move_zeros([false,1,0,1,2,0,1,3,"a"]) # returns[false,1,1,2,1,3,"a",0,0] 
```

My solution:

```
def move_zeros(array):
    a=[x for x in array if x!=0 or type(x)==bool]
    n=len(array)-len(a)
    for i in range(n):
        a.append(0)
    return a 
```

Clever solution NO.1:

```
def move_zeros(arr):
    l = [i for i in arr if isinstance(i, bool) or i!=0]
    return l+[0]*(len(arr)-len(l)) 
```

*这是本7级菜鸟做的第一个5级题，也没有想象中的那么难，可能是5级题中较为基础的一题。
此题的难点在于如何在删除0时留下同样值为0的False。remove(x)函数会删除第一个出现的值为x的元素，因此在本题上较难施展，得益于前两天看到了不删改只挑选的思路，在设定完条件后便实现了删改的效果。
除此之外，还有一个小知识点，通过`a+[x]*n`即可在a列表后添加n个同样的x元素，减少了一次for循环。*
**5.Create Phone Number**
Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.
Example:

```
create_phone_number([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]) # => returns "(123) 456-7890" 
```

My solution:

```
def create_phone_number(n):
    #your code here
    n.insert(0,'(')
    n.insert(4,') ')
    n.insert(8,'-')
    a=''.join([str(x) for x in n])
    return a 
```

Clever solution NO.1:

```
def create_phone_number(n):
  return "({}{}{}) {}{}{}-{}{}{}{}".format(*n) 
```

**5.String incrementer**
Your job is to write a function which increments a string, to create a new string.

If the string already ends with a number, the number should be incremented by 1.
If the string does not end with a number. the number 1 should be appended to the new string.

Examples:

```
foo -> foo1
foobar23 -> foobar24
foo0042 -> foo0043
foo9 -> foo10
foo099 -> foo100 
```

My solution:

```
def increment_string(strng):
    l=len(strng)-1
    s=list(strng)
    if l==-1:
        return "1"
    if strng[l]>'9' or strng[l]<'0':
        strng=strng+'1'
    else:
        if strng[l]!='9':
            s[l]=str(int(strng[l])+1)
        if strng[l]=='9':
            k=l
            nine=strng[k]
            while nine =='9':
                s[k]='0'
                k=k-1
                nine=strng[k]
            if nine<'9' and nine>='0':
                s[k]=str(int(s[k])+1)
            else:
                s.insert(k+1,'1')
        strng=''.join(s)
    return strng 
```

Clever solution NO.1:

```
def increment_string(strng):
    head = strng.rstrip('0123456789')
    tail = strng[len(head):]
    if tail == "": return strng+"1"
    return head + str(int(tail) + 1).zfill(len(tail)) 
```

此题苦思良久，但是方法较为繁琐，明天任务是看懂高分答案的算法。