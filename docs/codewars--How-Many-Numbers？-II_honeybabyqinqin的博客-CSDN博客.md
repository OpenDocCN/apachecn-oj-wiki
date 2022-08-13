<!--yml
category: codewars
date: 2022-08-13 11:48:14
-->

# codewars--How Many Numbers? II_honeybabyqinqin的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41871914/article/details/85892014?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-85892014.nonecase](https://blog.csdn.net/weixin_41871914/article/details/85892014?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-85892014.nonecase)

# How Many Numbers? II

[Click here to get problem.](https://www.codewars.com/kata/55f5efd21ad2b48895000040/train/python)

## Problem Description:

We want to find the numbers higher or equal than 1000 that the sum of every four consecutives digits cannot be higher than a certain given value. If the number is num = d1d2d3d4d5d6, and the maximum sum of 4 contiguous digits is maxSum, then:

d1 + d2 + d3 + d4 <= maxSum
d2 + d3 + d4 + d5 <= maxSum
d3 + d4 + d5 + d6 <= maxSum

For that purpose, we need to create a function, max_sumDig(), that receives nMax, as the max value of the interval to study (the range (1000, nMax) ), and a certain value, maxSum, the maximum sum that every four consecutive digits should be less or equal to. The function should output the following list with the data detailed bellow:

[(1), (2), (3)]

(1) - the amount of numbers that satisfy the constraint presented above

(2) - the closest number to the mean of the results, if there are more than one, the smallest number should be chosen.

(3) - the total sum of all the found numbers

Let’s see a case with all the details:

max_sumDig(2000, 3) -------> [11, 1110, 12555]

(1) -There are 11 found numbers: 1000, 1001, 1002, 1010, 1011, 1020, 1100, 1101, 1110, 1200 and 2000

(2) - The mean of all the found numbers is:
(1000 + 1001 + 1002 + 1010 + 1011 + 1020 + 1100 + 1101 + 1110 + 1200 + 2000) /11 = 1141.36363,
so 1110 is the number that is closest to that mean value.

(3) - 12555 is the sum of all the found numbers
1000 + 1001 + 1002 + 1010 + 1011 + 1020 + 1100 + 1101 + 1110 + 1200 + 2000 = 12555

Finally, let’s see another cases

max_sumDig(2000, 4) -----> [21, 1120, 23665]

max_sumDig(2000, 7) -----> [85, 1200, 99986]

max_sumDig(3000, 7) -----> [141, 1600, 220756]

Happy coding!!
![在这里插入图片描述](img/d803dcd3711cbef08bc9cd036e509c49.png)

###### Sample Tests:

```
test.describe("Example tests")
test.it("nMax = " + str(2000))
test.it("maxSum = " + str(3))
test.assert_equals(max_sumDig(2000, 3), [11, 1110, 12555])
test.it("nMax = " + str(2000))
test.it("maxSum = " + str(4))
test.assert_equals(max_sumDig(2000, 4), [21, 1120, 23665])
test.it("nMax = " + str(2000))
test.it("maxSum = " + str(7))
test.assert_equals(max_sumDig(2000, 7), [85, 1200, 99986])
test.it("nMax = " + str(3000))
test.it("maxSum = " + str(7))
test.assert_equals(max_sumDig(3000, 7), [141, 1600, 220756])
test.it("nMax = " + str(4000))
test.it("maxSum = " + str(4))
test.assert_equals(max_sumDig(4000, 4), [35, 2000, 58331]) 
```

* * *

## Version of Python:

![在这里插入图片描述](img/aa1f77ab7916dd87351c10befffad99b.png)
During my codes(method1,it’s python3.7,the codewars system make me only use 2.7.6)

* * *

## Solutions:

### Method1:

```
import numpy as np
def max_sumDig(nMax, maxSum):
    lists=[]
    for i in range(1000,nMax+1):
        list1=list(str(i))
        list1=list(map(int,list1))  
        list2=[np.sum(list1[i:i+4]) for i in range(len(list1)-3)]
        if max(list2)<=maxSum:
            lists.append(i)
    means=np.sum(lists)/len(lists)
    closest=min(lists, key=lambda x:abs(x-means))
    return [len(lists),closest,np.sum(lists)] 
```

Unfortunately, method1 runs time out.Also,when I run it in jupyter notebook, everything is ok.But when I run it in codewars, sample Test occurs unbelievable error.If you know why, thanks a lot for you to contact with me.

### Method2:

```
def check(num,max_sum):
    l = [int(i) for i in str(num)]
    for i in range(0,len(l) - 3):
        if sum(l[i:i+4]) > max_sum:return False
    return True

def max_sumDig(nMax, maxSum):
    found = [i for i in range(1000,nMax + 1) if check(i,maxSum)]
    mean = sum(found) / float(len(found))
    for i in range(len(found) - 1):
        if abs(mean - found[i]) < abs(mean - found[i + 1]):
            mean = found[i]
            break
    return [len(found), mean, sum(found)] 
```

### Method3:

```
def max_sumDig(nMax, maxSum, digits=4):
    values = [int(n) for n in map(str, xrange(10 ** (digits - 1), nMax + 1))
                        if all(sum(map(int, n[i:i+digits])) <= maxSum for i in range(len(n) - digits + 1))] 
    return [len(values), min(values, key=lambda n:abs(n - 1\. * sum(values) / len(values))), sum(values)] 
```

### Method4:

```
def max_sumDig(nMax, maxSum):

    def isGood(s):  return all(sum(map(int, str(s[i:i+4]))) <= maxSum for i in range(len(s)-3) )

    lst = [n for n in range(1000, nMax+1) if isGood(str(n))]
    s, l = sum(lst), len(lst)
    avg = 1.0*s/l
    iAvg = next( i for i,n in enumerate(lst) if n > avg )
    nearest = sorted(lst[iAvg-1:iAvg+1], key=lambda n: abs(n-avg))[0]
    return [l, nearest, s] 
```

### Method5:

```
def max_sumDig(nMax, maxSum):
    answers = []

    for i in range(1000, nMax + 1):
        good = True
        n = [int(x) for x in str(i)]
        for j in range(0, len(n)-3):
            if sum([n[j],n[j+1],n[j+2],n[j+3]]) > maxSum:
                good = False
        if good == True:
            answers.append(i)

    num, tot = len(answers), sum(answers)
    return [num, min(answers, key=lambda x: abs(x-(tot/float(num)))), tot] 
```

##### Method1 is written by me, and the others is made by some BIG PEOPLE.