<!--yml
category: codewars
date: 2022-08-13 12:20:51
-->

# 【Codewars python 5kyu】: Directions Reduction_小菜鸟快飞的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36362028/article/details/100547486?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-100547486.nonecase](https://blog.csdn.net/qq_36362028/article/details/100547486?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-100547486.nonecase)

# 问题描述：

### Once upon a time, on a way through the old wild west,…

… a man was given directions to go from one point to another. The directions were "NORTH", "SOUTH", "WEST", "EAST". Clearly "NORTH" and "SOUTH" are opposite, "WEST" and "EAST" too. Going to one direction and coming back the opposite direction is a needless effort. Since this is the wild west, with dreadfull weather and not much water, it's important to save yourself some energy, otherwise you might die of thirst!

### How I crossed the desert the smart way.

The directions given to the man are, for example, the following (depending on the language):

```
["NORTH", "SOUTH", "SOUTH", "EAST", "WEST", "NORTH", "WEST"].
```

or

```
{ "NORTH", "SOUTH", "SOUTH", "EAST", "WEST", "NORTH", "WEST" };
```

or

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

or

```
[West]
```

### Other examples:

In `["NORTH", "SOUTH", "EAST", "WEST"]`, the direction `"NORTH" + "SOUTH"` is going north and coming back *right away*. What a waste of time! Better to do nothing.

The path becomes `["EAST", "WEST"]`, now `"EAST"` and `"WEST"` annihilate each other, therefore, the final result is `[]` (nil in Clojure).

In ["NORTH", "EAST", "WEST", "SOUTH", "WEST", "WEST"], "NORTH" and "SOUTH" are not directly opposite but they become directly opposite after the reduction of "EAST" and "WEST" so the whole path is reducible to ["WEST", "WEST"].

### Task

Write a function `dirReduc` which will take an array of strings and returns an array of strings with the needless directions removed (W<->E or S<->N side by side).

*   The Haskell version takes a list of directions with `data Direction = North | East | West | South`.
*   The Clojure version returns nil when the path is reduced to nothing.
*   The Rust version takes a slice of `enum Direction {NORTH, SOUTH, EAST, WEST}`.

### See more examples in "Sample Tests:"

### Notes

*   Not all paths can be made simpler. The path ["NORTH", "WEST", "SOUTH", "EAST"] is not reducible. "NORTH" and "WEST", "WEST" and "SOUTH", "SOUTH" and "EAST" are not *directly*opposite of each other and can't become such. Hence the result path is itself : ["NORTH", "WEST", "SOUTH", "EAST"].

*   if you want to translate, please ask before translating.

# 代码实现:

```
#codewars第十四题
def dirReduc(arr):
    if len(arr) == 0 or len(arr) == 1: return arr
    i = 0
    j = 1
    while len(arr) > 1:
        if j >= len(arr): break
        if is_opposite(arr[i],arr[j]):
            arr.pop(j)
            arr.pop(i)
            i = 0
            j = 1
        else:
            i += 1
            j += 1
    return arr
def is_opposite(str1,str2):
    if (str1 == 'NORTH'and str2 == 'SOUTH') or (str1 =='SOUTH' and str2 == 'NORTH'):
        return True
    elif (str1 == 'EAST'and str2 == 'WEST') or (str1 =='WEST' and str2 == 'EAST'):
        return True
    else: return False

#另解  （利用栈啊）
opposite = {'NORTH': 'SOUTH', 'EAST': 'WEST', 'SOUTH': 'NORTH', 'WEST': 'EAST'}
def dirReduc(plan):
    new_plan = []
    for d in plan:
        if new_plan and new_plan[-1] == opposite[d]:
            new_plan.pop()
        else:
            new_plan.append(d)
    return new_plan
u=["NORTH", "WEST", "SOUTH", "EAST"]
dirReduc(u)
```