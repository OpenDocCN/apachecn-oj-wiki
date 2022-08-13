<!--yml
category: codewars
date: 2022-08-13 11:51:45
-->

# CodeWars: [5 kyu] Perimeter of squares in a rectangle_lkangkang的博客-CSDN博客

> 来源：[https://blog.csdn.net/lkangkang/article/details/82721865?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-82721865.nonecase](https://blog.csdn.net/lkangkang/article/details/82721865?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-82721865.nonecase)

The drawing shows 6 squares the sides of which have a length of 1, 1, 2, 3, 5, 8\. It's easy to see that the sum of the perimeters of these squares is : `4 * (1 + 1 + 2 + 3 + 5 + 8) = 4 * 20 = 80`

`//给出了一个序列，以序列为边长的正方形的周长和是多少`

Could you give the sum of the perimeters of all the squares in a rectangle when there are n + 1 squares disposed in the same manner as in the drawing:

//当有n+1个正方形行时，周长是多少

![alternative text](img/8be90235812787132eb6b27a420b5a24.png)

#Hint: See Fibonacci sequence

#Ref: [http://oeis.org/A000045](http://oeis.org/A000045)

The function perimeter has for parameter n where n + 1 is the number of squares (they are numbered from 0 to n) and returns the total perimeter of all the squares.

//函数的参数为n，n+1是正方形的个数，返回所有正方形的周长和

```
perimeter(5)  should return 80
perimeter(7)  should return 216
```

my solution:

递归的话遇到大数会运行超时，以空间换时间，保存之前已经计算过的 Fibonacci数。

[lkang](https://www.codewars.com/users/lkang)

```
 def perimeter(n):
    #Fibonacci sequence
    a=[]
    a.append(1)
    a.append(1)
    for i in range(2,n+1):
        a.append(a[i-1]+a[i-2])
    #
    return int(4*sum(a)) 
```

cleverest solution:

思路相同，极简的写法。省去了我用的列表空间，转为每得出一个数就加上去。

[lechevalier](https://www.codewars.com/users/lechevalier)

```
def perimeter(n):
    a, b = 1, 2
    while n:
        a, b, n = b, a + b, n - 1
    return 4 * (b - 1)
```