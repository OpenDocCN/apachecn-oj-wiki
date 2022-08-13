<!--yml
category: codewars
date: 2022-08-13 11:34:56
-->

# codewars【2】_幻梦鸵鸟的博客-CSDN博客

> 来源：[https://blog.csdn.net/i897355249/article/details/99076077?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-99076077.142^v40^control,185^v2^control](https://blog.csdn.net/i897355249/article/details/99076077?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-99076077.142^v40^control,185^v2^control)

**1.Growth of a Population**
In a small town the population is p0 = 1000 at the beginning of a year. The population
regularly increases by 2 percent per year and moreover 50 new inhabitants per year
come to live in the town.
How many years does the town need to see its population
greater or equal to p = 1200 inhabitants?

```
At the end of the first year there will be: 
1000 + 1000 * 0.02 + 50 => 1070 inhabitants

At the end of the 2nd year there will be: 
1070 + 1070 * 0.02 + 50 => 1141 inhabitants (number of inhabitants is an integer)

At the end of the 3rd year there will be:
1141 + 1141 * 0.02 + 50 => 1213

It will need 3 entire years. 
```

More generally given parameters:

```
p0, percent, aug (inhabitants coming or leaving each year), p (population to surpass) 
```

the function `nb_year`should return n number of entire years needed to
get a population greater or equal to p.
`aug` is an integer, percent a positive or null number, p0 and p are positive integers (> 0)

```
the function nb_year should return n number of entire years needed to
get a population greater or equal to p.
aug is an integer, percent a positive or null number, p0 and p are positive integers (> 0) 
```

Note: Don’t forget to convert the percent parameter as a percentage in the body of your function: if the parameter percent is 2 you have to convert it to 0.02.

My solution:

```
def nb_year(p0, percent, aug, p):
    # your code
    p1=p0
    k=0
    while p1<p:
        p1=p1*(1+percent/100)+aug
        k=k+1
    return 
```

Clever solution NO.1:

```
def nb_year(population, percent, aug, target):
    year = 0
    while population < target:
        population += population * percent / 100\. + aug
        year += 1
    return year 
```

**2.Array.diff**
Your goal in this kata is to implement a difference function, which subtracts one list from another and returns the result.
It should remove all values from list a, which are present in list b.

```
array_diff([1,2],[1]) == [2] 
```

If a value is present in `b`, all of its occurrences must be removed from the other:

```
array_diff([1,2,2,2,3],[2]) == [1,3] 
```

My solution:

```
from copy import deepcopy
def array_diff(a, b):
    #your code here
    c=deepcopy(a)
    for i in a:
        if i in b:
            c.remove(i)
    return c 
```

Clever solution NO.1:

```
def array_diff(a, b):
    return [x for x in a if x not in b] 
```

*此题是我8级菜鸟尝试的第一个6级题，实际感觉并没有想象的难。但是我仍然遇到了一个新问题，有了新理解。*

```
for i in a 
```

*这个for循环实质上是按照下标进行遍历的，如果在遍历途中，对a进行修改，就无法实现完全遍历。
举个例子*

```
a=[1,2,3,4,5]
for i in a:
	a.remove(i)
print(a) 
```

*得出结果为*

```
[2,4] 
```

*当删除下标为0的元素时，下标为1的元素变为了下标为0的元素，从而当下标遍历到1时，将会访问原先下标为2的元素。
解决这一问题的方法是使用deepcopy()函数，不是在目标列表上进行修改，而是对目标列表进行遍历时候，在deepcopy得到的列表上进行删改，从而既能完整遍历，又能成功删改。注意这里一定要使用deepcopy，如果只是简单的用c=a，a的值将会随c的改变而改变。
Clever solution的方法则更为精炼，不进行删改，只进行选择，也是我一直想要模仿学习的思路。*
**3.Unique In Order**
Implement the function unique_in_order which takes as argument a sequence and returns a list of items without any elements with the same value next to each other and preserving the original order of elements.
For example:

```
unique_in_order('AAAABBBCCDAABBB') == ['A', 'B', 'C', 'D', 'A', 'B']
unique_in_order('ABBCcAD')         == ['A', 'B', 'C', 'c', 'A', 'D']
unique_in_order([1,2,2,3,3])       == [1,2,3] 
```

My solution:

```
def unique_in_order(iterable):
    s=[]
    t=list(iterable)
    l=len(t)
    if l>=1:
        for i in range((l-1)):
            if t[i]!=t[i+1]:
                s.append(t[i])
        s.append(t[l-1])
        return s
    else:
        return []
    pass 
```

Clever solution NO.1:

```
def unique_in_order(iterable):
    result = []
    prev = None
    for char in iterable[0:]:
        if char != prev:
            result.append(char)
            prev = char
    return result 
```

Clever solution NO.2:

```
from itertools import groupby

def unique_in_order(iterable):
    return [k for (k, _) in groupby(iterable)] 
```

*第二个答案中的groupby函数用法还需要学习，明日学习任务+1,任重道远。*