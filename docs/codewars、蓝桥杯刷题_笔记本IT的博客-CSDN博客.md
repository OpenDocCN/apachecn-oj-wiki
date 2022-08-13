<!--yml
category: codewars
date: 2022-08-13 11:44:01
-->

# codewars、蓝桥杯刷题_笔记本IT的博客-CSDN博客

> 来源：[https://blog.csdn.net/httpsssss/article/details/115608845?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-115608845.nonecase](https://blog.csdn.net/httpsssss/article/details/115608845?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-115608845.nonecase)

You are going to be given an array of integers. Your job is to take that array and find an index N where the sum of the integers to the left of N is equal to the sum of the integers to the right of N. If there is no index that would make this happen, return -1.

For example:

Let’s say you are given the array {1,2,3,4,3,2,1}:
Your function will return the index 3, because at the 3rd position of the array, the sum of left side of the index ({1,2,3}) and the sum of the right side of the index ({3,2,1}) both equal 6.

```
def find_even_index(arr):
    list2 = arr.strip('{}').split(',')
    list1 = list(map(int, list2))
    len1 = len(list1)
    for i in range(1, len1 - 1):
        sum1 = sum(list1[0:i])
        sum2 = sum(list1[i + 1:len1])
        if sum1 == sum2:
            return list1.index(list1[i])

arr = input('shuru:')
print(find_even_index(arr)) 
```

题目描述
回形取数就是沿矩阵的边取数，若当前方向上无数可取或已经取过，则左转90度。一开始位于矩阵左上角，方向向下。
输入
输入第一行是两个不超过200的正整数m, n，表示矩阵的行和列。接下来m行每行n个整数，表示这个矩阵。
输出
输出只有一行，共mn个数，为输入矩阵回形取数得到的结果。数之间用一个空格分隔，行末不要有多余的空格。
样例输入
3 3
1 2 3
4 5 6
7 8 9
样例输出
1 4 7 8 9 6 3 2 5

```
import math  
r,c=map(int,input().split())
list1=[]
ans=[]
for i in range(0,r):
    list1.append(input().split())
for j in range(0,math.ceil(min(r,c)/2)):
    for x in range(j,r-j):
        ans.append(list1[x][j])
    for y in range(j+1,c-j):
        ans.append(list1[r-1-j][y])
    if c-1>2*j:
        for p in range(r-j-2,j-1,-1):
            ans.append(list1[p][c-1-j])
    if r-1>2*j:
        for q in range(c-j-2,j,-1):
            ans.append(list1[j][q])
for x in ans:
    print(x,'',end='') 
```

[转载](https://blog.csdn.net/Harry______/article/details/110678531)