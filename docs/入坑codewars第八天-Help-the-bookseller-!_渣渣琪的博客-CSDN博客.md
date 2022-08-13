<!--yml
category: codewars
date: 2022-08-13 11:43:06
-->

# 入坑codewars第八天-Help the bookseller !_渣渣琪的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_37341950/article/details/84843405?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-84843405.nonecase](https://blog.csdn.net/sinat_37341950/article/details/84843405?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-84843405.nonecase)

今天只写了一道题不容易呀，实在不懂输出格式，于是想办法凑出来的……

题目：

A bookseller has lots of books classified in 26 categories labeled A, B, ... Z. Each book has a code c of 3, 4, 5 or more capitals letters. The 1st letter of a code is the capital letter of the book category. In the bookseller's stocklist each code c is followed by a space and by a positive integer n (int n >= 0) which indicates the quantity of books of this code in stock.

For example an extract of one of the stocklists could be:

L = {"ABART 20", "CDXEF 50", "BKWRK 25", "BTSQZ 89", "DRTYM 60"}.

or

L = ["ABART 20", "CDXEF 50", "BKWRK 25", "BTSQZ 89", "DRTYM 60"] or ....

You will be given a stocklist (e.g. : L) and a list of categories in capital letters e.g :

M = {"A", "B", "C", "W"}

or

M = ["A", "B", "C", "W"] or ...

and your task is to find all the books of L with codes belonging to each category of M and to sum their quantity according to each category.

For the lists L and M of example you have to return the string (in Haskell/Clojure a list of pairs):

(A : 20) - (B : 114) - (C : 50) - (W : 0)

where A, B, C, W are the categories, 20 is the sum of the unique book of category A, 114 the sum corresponding to "BKWRK" and "BTSQZ", 50 corresponding to "CDXEF" and 0 to category 'W' since there are no code beginning with W.

If L or M are empty return string is `""` (Clojure should return an empty array instead).

```
题意就是：
输入：
b = ["ABAR 200", "CDXE 500", "BKWR 250", "BTSQ 890", "DRTY 600"]
c = ["A", "B"]
输入b代表书类别，比如ABAR是看首字母，首字母是A代表A类，后面跟着数字代表此类的藏书本数；
输入c代表需要计算这些类的本数，比如这里是A、B类因此在b中找A、B类的分别计数；
```

解题思路：

```
我的思路是：
（1）用字典存储，类别+本数；比如A类作为键，本数作为它的值；
（2）然后就遍历，如果是c中的键则它的值就加上b中字符串后面的数；这里的数用了正则表达式分割处理，具体可参考代码
（3）当都为零时则输出空字符串
（4）为了和输出一样我用了字符串连接处理
```

代码如下：

```
import re
def stock_list(listOfArt, listOfCat):
    dict = {}
    string1 = ""
    for x in listOfCat:
        dict[x] = 0
    for x in listOfCat:
        for y in listOfArt:
            if y[0] == x:
                a = int(re.sub("\D","",y))
                dict[x]=dict[x]+a
        string1=string1+"("+x+" : "+str(dict[x])+")"+" - "
    if sum(dict.values()) == 0:
        return "";
    string1=string1[:-3]
    return string1
```

上几个大神代码吧：

```
from collections import Counter

def stock_list(listOfArt, listOfCat):
    if not listOfArt:
        return ''
    codePos = listOfArt[0].index(' ') + 1
    cnt = Counter()
    for s in listOfArt:
        cnt[s[0]] += int(s[codePos:])
    return ' - '.join('({} : {})'.format(cat, cnt[cat]) for cat in listOfCat)
```

```
def stock_list(listOfArt, listOfCat):
    if (len(listOfArt) == 0) or (len(listOfCat) == 0):
        return ""
    result = ""
    for cat in listOfCat:
        total = 0
        for book in listOfArt:
            if (book[0] == cat[0]):
                total += int(book.split(" ")[1])
        if (len(result) != 0):
            result += " - "
        result += "(" + str(cat) + " : " + str(total) + ")"
    return result
```

```
def stock_list(stocklist, categories):
    if not stocklist or not categories:
        return ""
    return " - ".join(
        "({} : {})".format(
            category,
            sum(int(item.split()[1]) for item in stocklist if item[0] == category))
        for category in categories)
```