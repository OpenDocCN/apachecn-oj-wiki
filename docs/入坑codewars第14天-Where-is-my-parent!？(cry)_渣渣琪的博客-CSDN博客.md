<!--yml
category: codewars
date: 2022-08-13 11:51:12
-->

# 入坑codewars第14天-Where is my parent!?(cry)_渣渣琪的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_37341950/article/details/84990665?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-84990665.nonecase](https://blog.csdn.net/sinat_37341950/article/details/84990665?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-84990665.nonecase)

题目：

Mothers arranged dance party for children in school.On that party there are only mothers and their children.All are having great fun on dancing floor when suddenly all lights went out.Its dark night and no one can see eachother.But you were flying nearby and you can see in the dark and have ability to teleport people anywhere you want.

Legend:

-Uppercase letters stands for mothers,lowercase stand for their children. I.E "A" mothers children are "aaaa".
-Function input:String contain only letters,Uppercase letters are unique.

Task:

Place all people in alphabetical order where Mothers are followed by their children.I.E "aAbaBb" => "AaaBbb".

题意：

```
题意就是将所有的字母按照字母顺序排列，并且大写字母在前面；比如："abBA"——>"AaBb";
```

代码如下：

```
def find_children(dancing_brigade):
    list1=list(dancing_brigade)
    list1=sorted(list1, key=lambda c: (c.lower(),c.islower()))
    #sorted()根据每个字符的序数排序。大写字母的序号低于全部小写字母。
    #c将由('c', 1)进行分类和C由('c', 0)排序。按照第二位排序
    return "".join(list1)
```

```
#lamda就相当于一个f，lamda（x）相当于 f（x）

a = [(1, 2), (4, 1), (9, 10), (13, -3)]
    a.sort(key=lambda x: x[1])

    print(a)
    # Output: [(13, -3), (4, 1), (1, 2), (9, 10)]
```

学到了lambda 表达式，很绝妙的运用。感谢[https://stackoverrun.com/cn/q/9997188](https://stackoverrun.com/cn/q/9997188)的解释。

看看大神的代码：

```
def find_children(dancing_brigade):
    return ''.join(sorted(dancing_brigade,key=lambda c:(c.upper(),c.islower())))
```

精简的代码，很巧妙。sorted就是变成列表，因此我的写法就多此一举，我以为要先转成列表才能用sorted。 

第二题：

Create a function that accepts dimensions, of Rows x Columns, as parameters in order to create a multiplication table sized according to the given dimensions. **The return value of the function must be an array, and the numbers must be Fixnums, NOT strings.

Example:

multiplication_table(3,3)

1 2 3
2 4 6
3 6 9

-->[[1,2,3],[2,4,6],[3,6,9]]

Each value on the table should be equal to the value of multiplying the number in its first row times the number in its first column.

题意：

```
意思就是输入n行数和m列数，输出n行m列二维数组,且每一行的每个数都是第一个数的倍数，规律可见例子。
比如[2,2]——>[[1,2],[2,4]]
```

代码如下：

```
def multiplication_table(row,col):
    list1=[]
    list2=[]
    for i in range(0,row):
        a=i+1
        for j in range(0,col):
            list1.append(a*(j+1))
        list2.append(list1)
        list1=[]
    return list2
```

看看大神的精简代码：

```
def multiplication_table(row,col):
    return [[(i+1)*(j+1) for j in range(col)] for i in range(row)]
```

发现大神的思路比我好多了，这个规律就是每一个数都是行号乘以列号，因为是从0开始因此要用（i+1）*（j+1）；还是要开始学列表推导式，遇到循环学会用列表推导式！