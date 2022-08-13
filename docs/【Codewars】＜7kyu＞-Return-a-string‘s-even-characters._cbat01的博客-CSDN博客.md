<!--yml
category: codewars
date: 2022-08-13 11:42:55
-->

# 【Codewars】＜7kyu＞ Return a string‘s even characters._cbat01的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_36270908/article/details/111871942?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-29-111871942-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_36270908/article/details/111871942?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-29-111871942-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## 题目

> Write a function that returns a sequence (index begins with 1) of all the even characters from a string. If the string is smaller than two characters or longer than 100 characters, the function should return “invalid string”.
> 
> 编写一个函数，返回字符串中所有偶数位置的字符（索引以1开头）。如果字符串小于两个字符或长于100个字符，则函数应返回“invalid string”。

## 例子

```
"abcdefghijklm" --> ["b", "d", "f", "h", "j", "l"]
"a"             --> "invalid string" 
```

## 题解一

```
 function evenChars(string) {
    if(string.length < 2 || string.length > 100) return 'invalid string';
    var arr = [];
    for(let i=0;i<[...string].length;i++){  
        if(i%2 == 1) arr.push([...string][i]);
    }
    return arr;
} 
```

## 题解二

```
 function evenChars(string) {
    return (string.length < 2 || string.length > 100) ? 'invalid string' : [...string].filter((value,index) => index%2)
} 
```