<!--yml
category: codewars
date: 2022-08-13 11:26:56
-->

# 【萌新初学者】CodeWars战地笔记（JavaScript）_我落泪 情绪零碎的博客-CSDN博客_codewars使用教程

> 来源：[https://blog.csdn.net/m0_46690177/article/details/120210178?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-120210178.142^v40^control,185^v2^control](https://blog.csdn.net/m0_46690177/article/details/120210178?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-120210178.142^v40^control,185^v2^control)

最近发现了CodeWars这个网站，作为一个学习JavaScript的萌新，希望通过这个网站的练习来提升自己的代码水平。这篇文章是我在CodeWars解题以及浏览高赞答案时做的一些笔记，避免遗忘。笔记的内容基础得不能再基础了，单纯是自己记自己看的，希望大佬们不要取笑…

一、c.charCodeAt()将返回number类型的c的ASCII码，str.fromCharCode(num1, num2, num3 …)接受一个或多个ASCII码作为参数，返回这些ASCII码对应的字符拼接的字符串。实现字符与ASCII码的互相转化。

二、arr.join()将数组拼接为字符串，参数为两个数组元素之间的连接符。

三、str.split()将字符串切割为数组，参数为切割的标识符。

四、arr.map()方法需要检查arr是否为数组，因此有时要将arr改为(arr || [])，避免出现error。

五、map方法的第二个参数（可选）为index，第三个参数（可选）为元素所在的数组对象。

六、match方法的返回值为数组，参数中正则表达式后g表示全局匹配（返回所有匹配结果），i表示忽略大小写。

七、indexOf方法返回的是参数第一次出现时的index。

八、splice方法返回的是数组中被删除的部分而非剩余部分，第一个参数为所要删除部分的起始index，第二个为结尾index，参数为负数则index倒序计数，为非负数则index正序计数。

九、slice方法返回值为从字符串中取出的部分，第一个参数为所要取出部分的起始index，第二个为结尾index，参数为负数则index倒序计数，为非负数则index正序计数。

十、sort方法对数字升序排序：

```
numbers.sort((a, b) => {return a - b;}) 
```

降序排序：

```
numbers.sort((a, b) => {return b - a;}) 
```

十一、计算numbers数组最小值：Math.min.apply(null, numbers)
最大值：Math.max.apply(null, numbers)

十二、push和pop用于数组结尾，shift和unshift用于开头。

十三、toString方法的可选参数为所转化字符串的进制，例如num.toString(2)会将num转化为其二进制形式的字符串。

十四、parseInt可将字符串解析为整数。

十五、reduce的四个参数：初始值（上一次迭代后的结果），当前参与计算的值，当前值的索引，当前数组对象。

十六、善用replace方法替换字符串。

十七、Number.isInteger(num)方法可以判断num是否为整数。

十八、str.repeat(n)方法返回将str重复n次后拼接成的字符串。

十九、善用lastIndexOf方法，配合indexOf方法锁定数组中的某个位置。