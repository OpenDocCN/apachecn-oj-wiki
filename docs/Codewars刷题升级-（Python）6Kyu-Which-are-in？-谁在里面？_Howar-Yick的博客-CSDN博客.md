<!--yml
category: codewars
date: 2022-08-13 11:51:28
-->

# Codewars刷题升级 （Python）6Kyu Which are in? 谁在里面？_Howar Yick的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41432655/article/details/91877823?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-91877823.nonecase](https://blog.csdn.net/weixin_41432655/article/details/91877823?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-91877823.nonecase)

**题目描述：**

> Given two arrays of strings a1 and a2 return a sorted array r in
> lexicographical order of the strings of a1 which are substrings of
> strings of a2.
> 给定两个字符串列表：a1和a2,返回一个按字典顺序排序的字符串列表r，r列表中的字符串是a1里的元素且为a2的字符串。

**#Example 1:
示例一：**

> a1 = [“arp”, “live”, “strong”]
> a2 = [“lively”, “alive”, “harp”,“sharp”, “armstrong”]
> returns [“arp”, “live”, “strong”]

**#Example 2:
示例二：**

> a1 = [“tarp”, “mice”, “bull”]
> a2 = [“lively”, “alive”, “harp”, “sharp”, “armstrong”]
> returns []

**Notes:
注意：**
Arrays are written in “general” notation. See “Your Test Cases” for examples in your language.
数组中字符串均为小写。
In Shell bash a1 and a2 are strings. The return is a string where words are separated by commas.
a1、a2为字符串列表，返回的字符串用逗号分隔。
Beware: r must be without duplicates.
r没有重复项
Don’t mutate the inputs.
不要改变输入

**解题思路：**
array1中元素遍历，分别判断是否包含在array2中，如包含且不在结果列表中，添加进去，最后在把结果列表排下序。

**代码实现：**

```
def in_array(array1, array2):
    # your code
    result=[]
    for a in array1:
        for b in array2:
            if a in b and  a not in result:
                result.append(a)
                result.sort()
    return result 
```