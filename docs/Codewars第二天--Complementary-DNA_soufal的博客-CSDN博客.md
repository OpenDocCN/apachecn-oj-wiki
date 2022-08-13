<!--yml
category: codewars
date: 2022-08-13 11:48:32
-->

# Codewars第二天--Complementary DNA_soufal的博客-CSDN博客

> 来源：[https://blog.csdn.net/u011562123/article/details/81127379?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-81127379.nonecase](https://blog.csdn.net/u011562123/article/details/81127379?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-81127379.nonecase)

# Codewars第二天–Complementary DNA

开始在Codewars刷Python3题，发现基本知识都忘完了，边刷边复习边记录。

**8kyu>>7kyu**

```
Deoxyribonucleic acid (DNA) is a chemical found in the nucleus of cells and carries the "instructions" for the development and functioning of living organisms.

If you want to know more http://en.wikipedia.org/wiki/DNA

In DNA strings, symbols "A" and "T" are complements of each other, as "C" and "G". You have function with one side of the DNA (string, except for Haskell); you need to get the other complementary side. DNA strand is never empty or there is no DNA at all (again, except for Haskell).

DNA_strand ("ATTGC") # return "TAACG"

DNA_strand ("GTAT") # return "CATA"
```

这个题目其实很简单，就是执行一个DNA转RNA的过程，给定一个DNA单链字符串，输出与之对应的RNA字符串。

> 开始自己想得很复杂了，想着弄成列表，结果输出还要转换成字符串。。。

在这里只需要写一个类似switch的判断就好了，然后再用`join()`把每一个转换好的RNA字符链接成字符串输出就好了。
代码如下：

```
def DNA_strand(dna):

    my = {
            "A" : "T",
            "T" : "A",
            "C" : "G",
            "G" : "C",
            }
    return "".join(my[i] for i in dna)
```

代码中`my` 实现了对输入的DNA字符串进行转换的过程。

* * *

`join()`用法：
**用于将序列中的元素以指定的字符链接生成一个新的字符串。也就是使用它之后生成的只能是字符串。**

```
str.join(sequence)
```

前面的`str`指的是使用什么字符来连接需要连接的元素序列`sequence`。
这里我们不需要任何字符来连接就默认`""`。