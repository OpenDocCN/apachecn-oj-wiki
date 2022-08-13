<!--yml
category: codewars
date: 2022-08-13 11:26:28
-->

# codewars 算法题小结（转载）_哈里 谢顿的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_49497991/article/details/121667798?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-121667798.142^v40^control,185^v2^control](https://blog.csdn.net/weixin_49497991/article/details/121667798?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-121667798.142^v40^control,185^v2^control)

Codewars刷题升级 （Python）
***6Kyu ***Array.diff*** 数组的不同之处***

题目描述：

Your goal in this kata is to implement a difference function, which subtracts one list from another and returns the result.
此训练的目的是制定一个差别函数，用一个列表减去另一个列表，并返回结果。

It should remove all values from list a, which are present in list b.
它应该从列表a中删除所有出现在列表b中的值。

array_diff([1,2],[1]) == [2]
1
If a value is present in b, all of its occurrences must be removed from the other:
如果一个值在b中出现，所有在a中出现的这个值都要删除。

array_diff([1,2,2,2,3],[2]) == [1,3]
1
解题思路：
用列表推导式很容易是实现这个函数

代码实现：

```
def array_diff(a, b):

    return [x for x in a if x not in b] 
```

————————————————

**7Kyu ******Disemvowel Trolls***
“Trolls are attacking your comment section!
A common way to deal with this situation is to remove all of the vowels from the trolls’ comments, neutralizing the threat.
Your task is to write a function that takes a string and return a new string with all vowels removed.
For example, the string “This website is for losers LOL!” would become “Ths wbst s fr lsrs LL!”.
Note: for this kata y isn’t considered a vowel.”
题目简述
入参：字符串
功能：移除字符串中所有的元音字母，返回结果字符串

***【Codewars python 7kyu】: List Filtering***
问题描述：
In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.
在这个kata中，您将创建一个函数，该函数接受一个非负整数和字符串列表，并返回一个过滤掉字符串的新列表。
Example：
filter_list([1,2,‘a’,‘b’]) == [1,2]
filter_list([1,‘a’,‘b’,0,15]) == [1,0,15]
filter_list([1,2,‘aasf’,‘1’,‘123’,123]) == [1,2,123]
代码实现：
#codewars第三题：

```
def filter_list(l):
    _length = len(l)
    j = 0
    new_l = []  
    for i in range(0,_length):
        if type(l[i]) == str or l[i] < 0:
            continue
        else:
            new_l.append(l[i])  
            j += 1
    return new_l 
```

#第二种解决方法

```
def filter_list(l):
    return [x for x in l if type(x) is not str] 
```

#第三种方法

```
def filter_list(l):
    return [i for i in l if not isinstance(i, str)]
filter_list([1,2,'aasf','1','123',123]) 
```

***6 kyu Equal Sides Of An Array***
您将得到一个整数数组。您的任务是获取该数组并找到一个索引N，其中N左边的整数之和等于N右边的整数之和。如果没有索引，则返回-1。
例如：
假设你得到了数组{1,2,3,4,3,2,1}：
函数将返回索引3，因为在数组的第三个位置，索引的左侧（{1,2,3}）和索引的右侧（{3,2,1}）的和都等于6。
让我们看另一个。
您将获得数组{1100,50，-51,1,1}：
函数将返回索引1，因为在数组的第一个位置，索引左侧（{1}）和索引右侧（{50，-51,1,1}）的和都等于1。
最后一个：
给你数组{20,10，-80,10,10,15,35}
在索引0处，左侧为{}
右边是{10，-80,10,10,15,35}
它们相加时都等于0。（在此问题中，空数组等于0）
索引0是左侧和右侧相等的位置。
注意：请记住，在大多数编程/脚本语言中，数组的索引从0开始。
输入：
长度为0<arr<1000的整数数组。数组中的数字可以是任何正整数或负整数。
输出：
最低索引N，其中N左侧的边等于N右侧的边。如果找不到符合这些规则的索引，则返回-1。
注:
如果给您一个包含多个答案的数组，请返回正确的最低索引。
用python的话太简单了，直接用sum(列表)，如果是C++自己构造方法可能会比较复杂一些。
在这里立个flag，以后真的该尽量利用C++了。

```
def find_even_index(arr):
    if sum(arr) == 0:
        return 0
    for i in range(len(arr)):
        if sum(arr[0:i]) == sum(arr[i+1:]):
            return i
    return -1 
```

————————————————

***6 kyu Create Phone Number***
codewars python Create Phone Number
编写一个函数，该函数接受10个整数（介于0和9之间）的数组，以电话号码的形式返回这些数字的字符串。

```
def create_phone_number(n):

    str1 = ""
    str2 = ""
    str3 = ""
    for i in range(len(n)):
        if 0 <= i < 3: 
            str1 += str(n[i])
        elif 3 <= i < 6:
            str2 += str(n[i])
        else:
            str3 += str(n[i])
    return "("+str1+") "+str2+"-"+str3 
```

```
Test.describe("Basic tests")
Test.assert_equals(create_phone_number([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]), "(123) 456-7890")
Test.assert_equals(create_phone_number([1, 1, 1, 1, 1, 1, 1, 1, 1, 1]), "(111) 111-1111")
Test.assert_equals(create_phone_number([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]), "(123) 456-7890")
Test.assert_equals(create_phone_number([0, 2, 3, 0, 5, 6, 0, 8, 9, 0]), "(023) 056-0890")
Test.assert_equals(create_phone_number([0, 0, 0, 0, 0, 0, 0, 0, 0, 0]), "(000) 000-0000") 
```

***6 kyu Format a string of names like ‘Bart, Lisa & Maggie’.***
给定：包含名称哈希的数组
Return：一个字符串，格式为名称列表，用逗号分隔，最后两个名称除外，后面两个名称应用符号分隔。
Example:

```
namelist([ {'name': 'Bart'}, {'name': 'Lisa'}, {'name': 'Maggie'} ])

namelist([ {'name': 'Bart'}, {'name': 'Lisa'} ])

namelist([ {'name': 'Bart'} ])

namelist([]) 
```

```
def namelist(names):

    toReturn = ''
    if(len(names) == 1):
        return names[0]['name']
    elif(len(names) == 2):
        toReturn = toReturn + names[0]['name'] + " & " + names[1]['name']
    elif(len(names) > 2):
        for i in range(0, len(names)-1):
            toReturn = toReturn + names[i]['name'] + ", "
        toReturn = toReturn[:-2] + " & " + names[len(names)-1]['name']
    return toReturn 
```

***7 kyu Mumbling***
This time no story, no theory. The examples below show you how to write function accum:
Examples:

```
accum("abcd") -> "A-Bb-Ccc-Dddd"
accum("RqaEzty") -> "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
accum("cwAt") -> "C-Ww-Aaa-Tttt" 
```

```
def accum(s):
    """
    检测传入大小写字母的字符串，按照如下规则输出
    accum("abcd") -> "A-Bb-Ccc-Dddd"
    accum("RqaEzty") -> "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
    accum("cwAt") -> "C-Ww-Aaa-Tttt"
    :param s: 传入字符串、只包含大小写
    :return: 输出字符串，按照第1个字符输出1次，第二个字母输出2次，依次往后，另外每个首字母大写，其他小写
    """
    s=list(s)   
    result=''   
    print(s)
    j=0
    for i in s:
        j += 1    
        i=i*j     
        i=i.title()   
        print(i)
        result=result+i+'-'   
        pass
    print(result)
    result=result.strip('-')    
    print(result)
    return result 
```

## ***6 kyu Sort the odd***

您将获得一个数字数组。您必须按升序对奇数进行排序，同时将偶数保留在其原始位置。
Examples

```
[7, 1]  =>  [1, 7]
[5, 8, 6, 3, 4]  =>  [3, 8, 6, 5, 4]
[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]  =>  [1, 8, 3, 6, 5, 4, 7, 2, 9, 0] 
```

简单方法

```
def sort_array(list1):  
    list2=[]    
    list3=[]     
    for i in range(len(list1)):      
       if list1[i] %2!=0:          
          list2.append(list1[i])        
          list3.append(i)    
    list2.sort()    
    for i in range(len(list2)):   
       list1[ list3[i] ]=list2[i]  
   return list1 
```

大神方法

```
def sort_array(arr):   
    odds = sorted((x for x in arr if x%2 != 0), reverse=True)   
    return [x if x%2==0 else odds.pop() for x in arr]
`注释：这种方法把不用去管相应奇数的索引值，奇妙！
list1.pop()
这个函数的用法，将列表中最后一个值去除，并作为返回值.``
```python 
```

***7 kyu Odd or Even?***
给定一个整数列表，确定其元素之和是奇数还是偶数。
以匹配“奇数”或“偶数”的字符串给出答案。
如果输入数组为空，则将其视为：[ 0 ]（具有零的数组）。
Examples:

```
Input: [0]
Output: "even"
Input: [0, 1, 4]
Output: "odd"
Input: [0, -1, -5]
Output: "even" 
```

第一种：

```
def even_or_odd(number):

  return 'Odd' if number % 2 else 'Even' 
```

第二种

```
def even_or_odd(number):
  return 'Even' if number % 2 == 0 else 'Odd' 
```

第三种

```
def even_or_odd(number):
  if number % 2 == 0:
    return "Even"
  else:
    return "Odd" 
```

第四种

```
def even_or_odd(number):
  return ["Even", "Odd"][number % 2] 
```

第五种

```
def even_or_odd(number):
    if number % 2:
        return "Odd"
    return "Even" 
```

第六种

```
def even_or_odd(number):
    status = ""
    if number % 2 == 0:
        status = "Even"
    else:
        status = "Odd"

    return status 
```

***6 kyu Stop gninnipS My sdroW!***
编写一个函数，该函数接受一个或多个单词的字符串，并返回相同的字符串，但所有五个或多个字母单词都颠倒（就像这个Kata的名称一样）。传入的字符串将仅由字母和空格组成。只有存在多个单词时，才会包含空格。

示例：spinWords（“嘿，勇士们”）=>返回“嘿，wollef sroirraw”spinWords（“这是一个测试”）=>返回“这是一个测试”spinWords（“这是另一个测试”）=>返回“这是雷托纳测试”

题目为反转字符串中单词长度大于等于5的单词。代码如下：
先使用split（）通过空格将每一个单词分给开来。

*   split()函数split(str=”“, num=string.count(str)) 以str为分隔符截取字符串，如果num有指定值，则仅截取num个字符串。
*   str – 分隔符，默认为所有的空字符，包括空格、换行(\n)、制表符(\t)等。
*   num – 分割次数。分割后的字符串转换为了list。
    字符串实现反转的方法：
*   使用字符串切片：result = s[::-1]
*   使用列表的reverse（）：l = list(s) result = “”.join(l.reverse())””

```
def spin_words(sentence):

    sentence = sentence.split(" ")
    return " ".join([i[::-1] if len(i) >= 5 else i for i in sentence]) 
```

最后再使用join 将每一个单词连接为一个字符串输出。

***7 kyu You’re a square!***
方格
你喜欢积木。你特别喜欢正方形的积木。你更喜欢的是把它们排列成一个正方形的积木！
然而，有时候，你不能把它们排列成正方形。相反，你会得到一个普通的矩形！那些该死的东西！如果你只是想知道，你现在是否在徒劳地工作…等等！就这样！你只需要检查你的积木数量是否是一个完美的正方形。
任务
给定一个整数，确定它是否是一个平方数：
在数学中，一个平方数或完美平方是一个整数的平方；换句话说，它是某个整数与自身的乘积。
测试总是使用一些整数，所以在动态类型语言中不必担心这一点。
Examples

```
-1  =>  false
 0  =>  true
 3  =>  false
 4  =>  true
25  =>  true
26  =>  false 
```

```
def is_square(n):    
    if n<0:
        return False
    elif n == 0:
        return True
    else:
        i = 1
        while i < n:
            m = i*i
            if m == n:
                return True
            elif m>n:
                return False
            else:
                i+=1 
```