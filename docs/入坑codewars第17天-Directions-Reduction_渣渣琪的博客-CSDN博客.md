<!--yml
category: codewars
date: 2022-08-13 11:43:46
-->

# 入坑codewars第17天-Directions Reduction_渣渣琪的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_37341950/article/details/85036388?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-85036388.nonecase](https://blog.csdn.net/sinat_37341950/article/details/85036388?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-85036388.nonecase)

# 题目：

# Once upon a time, on a way through the old wild west,…

… a man was given directions to go from one point to another. The directions were "NORTH", "SOUTH", "WEST", "EAST". Clearly "NORTH" and "SOUTH" are opposite, "WEST" and "EAST" too. Going to one direction and coming back the opposite direction is a needless effort. Since this is the wild west, with dreadfull weather and not much water, it's important to save yourself some energy, otherwise you might die of thirst!

## How I crossed the desert the smart way.

The directions given to the man are, for example, the following:

```
["NORTH", "SOUTH", "SOUTH", "EAST", "WEST", "NORTH", "WEST"]. 
```

or

```
{ "NORTH", "SOUTH", "SOUTH", "EAST", "WEST", "NORTH", "WEST" }; 
```

or (haskell)

```
[North, South, South, East, West, North, West] 
```

You can immediatly see that going "NORTH" and then "SOUTH" is not reasonable, better stay to the same place! So the task is to give to the man a simplified version of the plan. A better plan in this case is simply:

```
["WEST"] 
```

or

```
{ "WEST" } 
```

or (haskell)

```
[West] 
```

or (rust)

```
[WEST]; 
```

# Other examples:

In `["NORTH", "SOUTH", "EAST", "WEST"]`, the direction `"NORTH" + "SOUTH"` is going north and coming back *right away*. What a waste of time! Better to do nothing.

The path becomes `["EAST", "WEST"]`, now `"EAST"` and `"WEST"`annihilate each other, therefore, the final result is `[]` (nil in Clojure).

In ["NORTH", "EAST", "WEST", "SOUTH", "WEST", "WEST"], "NORTH" and "SOUTH" are not directly opposite but they become directly opposite after the reduction of "EAST" and "WEST" so the whole path is reducible to ["WEST", "WEST"].

# Task

Write a function `dirReduc` which will take an array of strings and returns an array of strings with the needless directions removed (W<->E or S<->N side by side).

The Haskell version takes a list of directions with `data Direction = North | East | West | South`. The Clojure version returns nil when the path is reduced to nothing. The Rust version takes a slice of `enum Direction {NORTH, SOUTH, EAST, WEST}`.

# Examples

```
dirReduc(@[@"NORTH", @"SOUTH", @"SOUTH", @"EAST", @"WEST", @"NORTH", @"WEST"]); // => @[@"WEST"]
dirReduc(@[@"NORTH", @"SOUTH", @"SOUTH", @"EAST", @"WEST", @"NORTH"]); // => @[] 
```

# See more examples in "Example Tests"

# Note

Not all paths can be made simpler. The path ["NORTH", "WEST", "SOUTH", "EAST"] is not reducible. "NORTH" and "WEST", "WEST" and "SOUTH", "SOUTH" and "EAST" are not directly opposite of each other and can't become such. Hence the result path is itself : ["NORTH", "WEST", "SOUTH", "EAST"].

题意：

```
题意就是
一个人被指示从一个地方去另一个地方。方向是“北”、“南”、“西”、“东”。显然，“北”和“南”是对立的，“西”和“东”也是对立的。朝一个方向去，又朝相反的方向回来，这是一种不必要的努力。因为这是蛮荒的西部，天气很糟糕，水也不多，所以一定要节约一些能量，否则你会渴死的!
你马上就能看到，先“北”再“南”是不合理的，还是呆在原地好!所以任务是给这个人一个简化版的计划。

(“北”、“南”、“东”、“西”)中，“北”+“南”的方向是向北，然后马上返回。真是浪费时间!最好什么也不做。
路径变成[东"、"西"]，现在"东"和"西"相互湮灭，因此，最终结果是[](Clojure中为nil)。
在[北"、"东"、"西"、"南"、"西"]中，"北"和"南"不是直接对立的，而是经过"东"和"西"的还原而成为直接对立的，所以整个路径可以还原为[西"、"西"]。

写一个函数dirReduc，它将取一个字符串数组，并返回一个字符串数组，去掉不必要的方向(W<->E或S<->N并排)。
Haskell版本采用一个方向列表，数据方向=北|东|西|南。当路径被还原为空时，Clojure版本返回nil。锈版采用了一个切片枚举方向{北，南，东，西}。

并不是所有的路径都可以简化。这条路(“北”、“西”、“南”、“东”)是不可简化的。“北”与“西”、“西”与“南”、“南”与“东”不是直接对立的，不可能成为对立的。因此，结果路径本身就是:[“北”、“西”、“南”、“东”]。
```

```
样例：
a = ["NORTH", "SOUTH", "SOUTH", "EAST", "WEST", "NORTH", "WEST"]
test.assert_equals(dirReduc(a), ['WEST'])
u=["NORTH", "WEST", "SOUTH", "EAST"]
test.assert_equals(dirReduc(u), ["NORTH", "WEST", "SOUTH", "EAST"])
```

思路：

```
思路很简单就是找相邻的两个列表元素的值
如果是相反的就删除；
返回最后的列表
```

代码如下：

这次一次就通过了，哈哈

```
def dirReduc(arr):
    length=len(arr)
    i=0
    while i<length-1:
        if (arr[i]=='NORTH'and arr[i+1]=='SOUTH') or (arr[i+1]=='NORTH'and arr[i]=='SOUTH') or (arr[i]=='EAST'and arr[i+1]=='WEST') or (arr[i+1]=='EAST'and arr[i]=='WEST'):
            del arr[i]
            del arr[i]
            length=length-2
            i=0
        else:
            i=i+1
    return arr
```

看看大神的精简代码：

```
def dirReduc(arr):
    dir = " ".join(arr)
    dir2 = dir.replace("NORTH SOUTH",'').replace("SOUTH NORTH",'').replace("EAST WEST",'').replace("WEST EAST",'')
    dir3 = dir2.split()
    return dirReduc(dir3) if len(dir3) < len(arr) else dir3
```

```
opposite = {'NORTH': 'SOUTH', 'EAST': 'WEST', 'SOUTH': 'NORTH', 'WEST': 'EAST'}

def dirReduc(plan):
    new_plan = []
    for d in plan:
        if new_plan and new_plan[-1] == opposite[d]:
            new_plan.pop()
        else:
            new_plan.append(d)
    return new_plan
```