<!--yml
category: codewars
date: 2022-08-13 11:51:25
-->

# [codewars][Python] 移动首字母_尉迟海棠的博客-CSDN博客

> 来源：[https://blog.csdn.net/GYK0812/article/details/102814177?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-102814177.nonecase](https://blog.csdn.net/GYK0812/article/details/102814177?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-102814177.nonecase)

题目：把每个单词的首字母移到单词结尾，并添加“ay”，输入新的字符串

Smart Answer:

string.isalnum()方法  --  如果 string 至少有一个字符并且所有字符都是字母或数字则返回 True,否则返回 False

```
def pig_it(text):
    lst = text.split()
    return ' '.join( [word[1:] + word[0] + 'ay' if word.isalnum() else word for word in lst])
```

My Answer:

思路和上面的一样

```
def pig_it(text):
    #your code here
    list1 = text.split(" ")   #把字符串分成一个新的列表
    list2 = []
    for each in list1:
        if each in ["!","?","/"]:
            list2.append(each)
        else:
            new_words = each[1:]+each[0]+"ay"
            list2.append(new_words)
        # print(each)
    str1 = " ".join(list2)
    return str1
```