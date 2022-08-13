<!--yml
category: codewars
date: 2022-08-13 11:45:08
-->

# codewars [Pascal's Triangle] 6kyu Pyhton_就是个弟弟的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_40541112/article/details/83058125?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-83058125.nonecase](https://blog.csdn.net/qq_40541112/article/details/83058125?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-83058125.nonecase)

## 问题描述：

Wikipedia article on Pascal’s Triangle: [http://en.wikipedia.org/wiki/Pascal’s_triangle](http://en.wikipedia.org/wiki/Pascal'%20rel=)

Write a function that, given a depth (n), returns a single-dimensional array/list representing Pascal’s Triangle to the n-th level.

For example:

```
pascals_triangle(4) == [1,1,1,1,2,1,1,3,3,1] 
```

## 问题解决：

```
def pascals_triangle(n):
  l=[]
  c=[]
  for i in range(n):
      l.append([])
      for j in range(i+1):
          if j in (0,i):
              l[i].append(1)
          else:
              l[i].append(l[i-1][j-1]+l[i-1][j])
  for i in range(len(l)):
       c+=l[i]
  return c 
```

其他解决方法：

```
def pascals_triangle(n):
  if n == 1:
      return [1]
  prev = pascals_triangle(n - 1)
  return prev + [1 if i == 0 or i == n -1 else prev[-i] + prev[-(i + 1)] 
              for i in range(n)] 
```

```
def pascals_triangle(n):
    # Check for these simpler answers before diving into the iteration:
    if n < 1 or type(n) != int:
        print("Input must be positive and an integer!")
        return None
    elif n == 1:
        return [1]
    elif n == 2:
        return [1, 1, 1]
    # Set up the rest of the function for when n >= 3:
    r = [1, 1, 1] # result stored here
    prev_row = [1, 1] # comparing to previous row
    for i in range(3, n + 1):
        row = [1] + [0 for j in range(1,i-1)] + [1] #set up the current working row
        for j in range(1, i - 1):
            row[j] = prev_row[j-1] + prev_row[j] # add the values from the previous row
        r += row # update the result
        prev_row = row # current row beomes previous row
    return r 
```