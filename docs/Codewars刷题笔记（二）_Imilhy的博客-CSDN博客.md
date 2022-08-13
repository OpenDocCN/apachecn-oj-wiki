<!--yml
category: codewars
date: 2022-08-13 11:39:41
-->

# Codewars刷题笔记（二）_Imilhy的博客-CSDN博客

> 来源：[https://blog.csdn.net/Imilhy/article/details/104308281?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-104308281.142^v40^control,185^v2^control](https://blog.csdn.net/Imilhy/article/details/104308281?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-104308281.142^v40^control,185^v2^control)

题目：
Given two arrays of strings a1 and a2 return a sorted array r in lexicographical order of the strings of a1 which are substrings of strings of a2.

#Example 1: a1 = [“arp”, “live”, “strong”]

a2 = [“lively”, “alive”, “harp”, “sharp”, “armstrong”]

returns [“arp”, “live”, “strong”]

#Example 2: a1 = [“tarp”, “mice”, “bull”]

a2 = [“lively”, “alive”, “harp”, “sharp”, “armstrong”]

returns []
Notes:
Arrays are written in “general” notation. See “Your Test Cases” for examples in your language.

In Shell bash a1 and a2 are strings. The return is a string where words are separated by commas.

Beware: r must be without duplicates.
Don’t mutate the inputs.
我的解答：

```
def in_array(array1, array2):

    list=[]
    str = ''.join(array2)
    for i in range(len(array1)):
        if array1[i] in str:
            list.append(array1[i])
        else:
            list=list
    return list.sort() 
```

这是我的原始解答，结果发现返回的列表总是为空，百思不得其解，后来才知道list对象调用自身的sort方法对自己进行排序，最终的结果是改变自身。而list.sort()函数返回值默认为None,所以这就是为什么返回值是None了，那么这个问题该如何解决呢？既然list.sort()函数改变的是其本身，那么我们就先调用这个函数，让list自身改变，再返回改变后的list不就好了，代码如下：

```
def in_array(array1, array2):

    list=[]
    str = ''.join(array2)
    for i in range(len(array1)):
        if array1[i] in str:
            list.append(array1[i])
        else:
            list=list
    list.sort()        
    return list 
```

基本样本测试通过，结果在进行所有的测试时，发现自己忘记了返回的List不能含有相同的元素，于是修改代码如下：

```
def in_array(array1, array2):

    list=[]
    str = ''.join(array2)
    array3=list(set(array1))
    for i in range(len(array3)):
        if array3[i] in str:
            list.append(array3[i])
        else:
            list=list
    list.sort()
    return list 
```

结果报错：
Traceback (most recent call last):
File “main.py”, line 6, in
test.assert_equals(in_array(a1, a2), r)
File “/home/codewarrior/solution.py”, line 5, in in_array
array3=list(set(array1))
TypeError: ‘list’ object is not callable

发现是自己的变量命名和调用的方法重名了，这确实是容易犯的错误，在以后变量命名的时候也要尽量避免，修改变量名：

```
def in_array(array1, array2):

    list1=[]
    str = ''.join(array2)
    array3=list(set(array1))
    for i in range(len(array3)):
        if array3[i] in str:
            list1.append(array3[i])
        else:
            list1=list1
    list1.sort()
    return list1 
```

测试通过