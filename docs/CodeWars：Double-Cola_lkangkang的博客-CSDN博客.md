<!--yml
category: codewars
date: 2022-08-13 11:47:24
-->

# CodeWars:Double Cola_lkangkang的博客-CSDN博客

> 来源：[https://blog.csdn.net/lkangkang/article/details/82687580?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-82687580.nonecase](https://blog.csdn.net/lkangkang/article/details/82687580?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-82687580.nonecase)

Sheldon, Leonard, Penny, Rajesh and Howard are in the queue for a "Double Cola" drink vending machine; there are no other people in the queue. The first one in the queue (Sheldon) buys a can, drinks it and doubles! The resulting two Sheldons go to the end of the queue. Then the next in the queue (Leonard) buys a can, drinks it and gets to the end of the queue as two Leonards, and so on.

For example, Penny drinks the third can of cola and the queue will look like this:

```
Rajesh, Howard, Sheldon, Sheldon, Leonard, Leonard, Penny, Penny 
```

Write a program that will return the name of the person who will drink the n-th cola.

Note that in the very beginning the queue looks like that:

```
Sheldon, Leonard, Penny, Rajesh, Howard 
```

##Input

The input data consist of an array which contains at least 1 name, and single integer n.

```
(1 ≤ n ≤ 1000000000). 
```

##Output / Examples Return the single line — the name of the person who drinks the n-th can of cola. The cans are numbered starting from 1\. Please note that you should spell the names like this: "Sheldon", "Leonard", "Penny", "Rajesh", "Howard" (without the quotes). In that order precisely the friends are in the queue initially.

```
whoIsNext(["Sheldon", "Leonard", "Penny", "Rajesh", "Howard"], 1)=="Sheldon"
whoIsNext(["Sheldon", "Leonard", "Penny", "Rajesh", "Howard"], 52)=="Penny"
whoIsNext(["Sheldon", "Leonard", "Penny", "Rajesh", "Howard"], 7230702951)=="Leonard"
```

my solution:

*   ```
    def whoIsNext(names, r):
        from math import log2
        n=int(log2(r/5+1))
        less=r-5*(1-2**n)/(1-2)
        location=less/(2**n)
        if location<=1:
            return names[0]
        elif location>1 and location<=2:
            return names[1]
        elif location>2 and location<=3:
            return names[2]
        elif location>3 and location<=4:
            return names[3]
        elif location>4 and location<=5:
            return names[4]
        else:
            return names[5] 
    ```

cleverest solution:

[Spencer-Zhang](https://www.codewars.com/users/Spencer-Zhang), [magnert](https://www.codewars.com/users/magnert), [Yazan24](https://www.codewars.com/users/Yazan24)

```
def whoIsNext(names, r):
    while r > 5:
        r = (r - 4) / 2
    return names[r-1]
```