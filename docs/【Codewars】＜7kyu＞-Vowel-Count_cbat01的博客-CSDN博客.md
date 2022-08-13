<!--yml
category: codewars
date: 2022-08-13 11:51:10
-->

# 【Codewars】＜7kyu＞ Vowel Count_cbat01的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_36270908/article/details/111562774?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-111562774.nonecase](https://blog.csdn.net/weixin_36270908/article/details/111562774?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-111562774.nonecase)

### 一、题目：

> Return the number (count) of vowels in the given string.
> 
> **这道题要实现的是返回字符串中的元音个数（a,e,i,o,u）**

### 二、例子：

```
getCount("abracadabra"), 5 
```

### 三、题解一：

```
 function getCount(str) {
    var vowelsCount = 0;

    var arr = str.split('');
    for(let i=0;i<arr.length;i++){
        if(arr[i] === 'a' || arr[i] === 'e' || arr[i] === 'i' || arr[i] === 'o' || arr[i] === 'u')
        vowelsCount++;
    }
    return vowelsCount;
} 
```

### 四、题解二：(Best Practices)

```
 function getCount(str) {
    return (str.match(/[aeiou]/ig) || []).length;
} 
```