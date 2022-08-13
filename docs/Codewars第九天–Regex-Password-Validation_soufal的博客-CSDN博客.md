<!--yml
category: codewars
date: 2022-08-13 11:46:07
-->

# Codewars第九天–Regex Password Validation_soufal的博客-CSDN博客

> 来源：[https://blog.csdn.net/u011562123/article/details/81948072?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-81948072.nonecase](https://blog.csdn.net/u011562123/article/details/81948072?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-81948072.nonecase)

## Codewars第九天–Regex Password Validation

一个很有意思的题目，只是要求写出一个正则表达式来判断输入的密码是否符合以下标准：
* 至少有六个字符长
* 包含一个大写字母
* 包含一个小写字母
* 包含一个数字
有效密码只能是字母数字字符。
相应的正则表达式如下：

```
regex="^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[^\W_]{6,}$"
```

```
^              
(?=.*?[a-z])   
(?=.*?[A-Z])   
(?=.*?[0-9])   
[A-Za-z\d]     
{6,}           
$ 
```