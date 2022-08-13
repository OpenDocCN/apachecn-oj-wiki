<!--yml
category: codewars
date: 2022-08-13 11:47:52
-->

# Codewars第八天--Good vs Evil_soufal的博客-CSDN博客

> 来源：[https://blog.csdn.net/u011562123/article/details/81911110?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-81911110.nonecase](https://blog.csdn.net/u011562123/article/details/81911110?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-81911110.nonecase)

## Codewars第八天–Good vs Evil

题目描述：

```
霍比特人：1
男子：2
精灵：3
矮人：3
老鹰队：4
巫师：10
在邪恶的一面，我们有：

兽人：1
男子：2
Wargs：2
哥布林：2
Uruk Hai：3
巨魔：5
巫师：10

输入：
该函数将给出两个参数。每个参数都是由单个空格分隔的字符串。每个字符串将包含善恶方面的每个种族的数量。

第一个参数将按以下顺序包含good的一侧的每个种族的计数：

霍比特人，男人，精灵，矮人，老鹰，巫师。
第二个参数将按以下顺序包含邪恶方面的每个种族的计数：

兽人，男人，Wargs，哥布林，乌鲁克海，巨魔，巫师。
所有值都是非负整数。由此产生的每一方的总和不会超过32位整数的限制。
输出：
通过他们的总的战斗力来判断哪一个势力将会在战斗中获胜.
```

开始时，所写的代码如下，通过记录输入的种族人数的索引去对应`value` 中的值，然后将他们相乘求和。
但是最后的结果永远会有6个`test` 通不过。例如：`{1 0 0 0 1 0},{0 0 0 0 0 1 0}` 。他们得到的正确结果应当是平手都为5，但是代码给的结果是`evil` 获胜了。通过输出他们具体的值发现，代码得出的结果是`good` 为2，`evil` 为5。
仔细查看代码发现，因为在这里我用的是索引去查找对应`worth` 中的值。而这个`test` 中不同位置上有着两个相同的值，使用`index()` 去找索引，他永远都只会返回索引0的值，找不到正确的位置，因此这样做事行不通的。

```
def goodVsEvil(good, evil):
    good_worth = [1, 2, 3, 3, 4, 10]
    evil_worth = [1, 2, 2, 2, 3, 5, 10]
    good = good.split()
    evil = evil.split()
    good_value = 0
    evil_value =0
    for i in good:
            index_g = int(good.index(i))
            good_value += int(i) * good_worth[index_g]
    for j in evil:
            index_e = int(evil.index(j))
            evil_value += int(j) * evil_worth[index_e]
    if good_value > evil_value:
        return 'Battle Result: Good triumphs over Evil'
    elif good_value < evil_value:
        return 'Battle Result: Evil eradicates all trace of Good'
    else:
        return 'Battle Result: No victor on this battle field' 
```

改进的代码如下，这里使用了`Python3` 的`zip` 函数，这个函数可以**将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的对象，这样做的好处是节约了不少的内存。** 他可以将这里的两个`good` 和`good_worth` 打包成一个元组，每个位置的值直接对应起来，不需要手动去查找`index` 。

```
def goodVsEvil(good, evil):
    good_worth = [1, 2, 3, 3, 4, 10]
    evil_worth = [1, 2, 2, 2, 3, 5, 10]
    good = good.split()
    evil = evil.split()
    good_value = 0
    evil_value =0
    for i,j in zip(good, good_worth):
            good_value += int(i) * j
    for i,j in zip(evil, evil_worth):
            evil_value += int(i) * j
    if good_value > evil_value:
        return 'Battle Result: Good triumphs over Evil'
    elif good_value < evil_value:
        return 'Battle Result: Evil eradicates all trace of Good'
    else:
        return 'Battle Result: No victor on this battle field' 
```