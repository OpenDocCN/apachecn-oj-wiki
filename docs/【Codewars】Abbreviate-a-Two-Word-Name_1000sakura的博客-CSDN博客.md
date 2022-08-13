<!--yml
category: codewars
date: 2022-08-13 11:48:53
-->

# 【Codewars】Abbreviate a Two Word Name_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/89791848?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-89791848.nonecase](https://blog.csdn.net/ecysakura/article/details/89791848?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-89791848.nonecase)

### Codewars里的 8kyu Kata。

### 题目说明：

> Write a function to convert a name into initials. This kata strictly takes two words with one space in between them.
> 
> The output should be two capital letters with a dot seperating them.
> 
> It should look like this:
> 
> `Sam Harris` => `S.H`
> 
> `Patrick Feeney` => `P.F`

把两个单词搞成缩写的形式。形如 Sam Harris -> S.H。

很简单的题目。

### 解题代码：

```
public class AbbreviateTwoWords {
    public static String abbrevName(String name) {
        //name = name.toUpperCase();
        //int index = name.indexOf(' ');
        //String ch = name.substring(index+1, index+2);
        //name = name.substring(0, 1).concat(".");
        //name = name.concat(ch);
        name = name.substring(0, 1).concat(".").concat(name.substring(name.indexOf(' ')+1, name.indexOf(' ')+2)).toUpperCase();
        return name;
    }
}
```

### 个人总结：

从简单开始刷起题目吧，这道题可以试试正则表达式。