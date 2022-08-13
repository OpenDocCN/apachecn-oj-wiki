<!--yml
category: codewars
date: 2022-08-13 11:41:45
-->

# CodeWars题目训练2【Python】_会飞的鸡仔的博客-CSDN博客

> 来源：[https://blog.csdn.net/kukukukuwo/article/details/79713874?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-22-79713874-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/kukukukuwo/article/details/79713874?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-22-79713874-null-null.142^v40^control,185^v2^control&utm_term=codewars)

**题目：** Convert boolean values to strings ‘Yes’ or ‘No’.
**等级：** 8 【最低一级】
**介绍：** Complete the method that takes a boolean value and return a “Yes” string for true, or a “No” string for false
**翻译：**大概意思就是用”Yes”字符串来代替布尔返回值”True”，用”No”字符串来代替布尔返回值”False”。

给定题目的代码：

```
def bool_to_word(boolean): 
```

测试代码：

```
Test.assert_equals(bool_to_word(True), 'Yes')
Test.assert_equals(bool_to_word(False), 'No')
```

博主解决思路：
使用两个if判断，如果值是”True”那么返回”Yes”，如果值是”False”，那么返回”No”。
代码：

```
def bool_to_word(boolean):

    if boolean == True:
        return 'Yes'
    elif boolean == False:
        return 'No'
```

最佳答案（由网友投票产生的）：

```
def bool_to_word(bool):
    return "Yes" if bool else "No"
```

**总结：**
可以看到，博主和最佳的代码量的区别了。这是因为博主忽略了，使用if 判断的时候，布尔值是可以直接用作条件的，因此不需要使用”==” 来判断，所以就多此一举了。
另外网友多将代码以一行的写法显示，但是注意使用博主注释的那个代码是行不通的：”#return ‘Yes’ if boolean == True elif boolean == False ‘No’”。
如果谁知道具体写法或者到底能不能使用这样的写法，请在下面留言，感激不尽。

有兴趣训练的代码的可以上去CodeWars官网：
www.codewars.com/r/z7grhQ