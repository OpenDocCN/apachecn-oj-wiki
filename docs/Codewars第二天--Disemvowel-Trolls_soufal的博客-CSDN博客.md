<!--yml
category: codewars
date: 2022-08-13 11:47:26
-->

# Codewars第二天--Disemvowel Trolls_soufal的博客-CSDN博客

> 来源：[https://blog.csdn.net/u011562123/article/details/81132223?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-81132223.nonecase](https://blog.csdn.net/u011562123/article/details/81132223?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-81132223.nonecase)

## Codewars第二天–Disemvowel Trolls

继续刷题，题目描述为：
`Trolls are attacking your comment section!
A common way to deal with this situation is to remove all of the vowels from the trolls' comments, neutralizing the threat.
Your task is to write a function that takes a string and return a new string with all vowels removed.
For example, the string "This website is for losers LOL!" would become "Ths wbst s fr lsrs LL!".
Note: for this kata y isn't considered a vowel.`

题目描述很好玩，和LOL有关。
要求是需要将评论中的**元音字母** 从字符串中删除。并返回删除后的字符串。并且y不算做元音。这个题也很简单，我们只需要找出字符串中的元音字母`aeiou` 及他们的大小形式`AEIOU` ，然后删除他们即可。

代码如下：

```
def disemvowel(string):
    s = 'aeiouAEIOU'
    for i in range(len(s)):
        string = string.replace(s[i], '')

    return string
```

创建一个元音字母构成的新字符，通过遍历使用`replace()` 将元音字母替换为`''` ，也就是空。