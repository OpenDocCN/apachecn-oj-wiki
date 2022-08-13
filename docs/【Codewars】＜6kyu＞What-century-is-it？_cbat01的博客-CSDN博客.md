<!--yml
category: codewars
date: 2022-08-13 11:42:22
-->

# 【Codewars】＜6kyu＞What century is it?_cbat01的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_36270908/article/details/111582291?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-11-111582291-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_36270908/article/details/111582291?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-11-111582291-null-null.142^v40^control,185^v2^control&utm_term=codewars)

### 题目：

> Return the century of the input year. The input will always be a 4 digit string, so there is no need for validation.
> 
> 返回输入年份的世纪。输入总是一个4位数的字符串，因此不需要验证。

### 示例：

```
"1999" --> "20th"
"2011" --> "21st"
"2154" --> "22nd"
"2259" --> "23rd"
"1124" --> "12th"
"2000" --> "20th" 
```

### 题解一：

```
 function whatCentury(year){
    var r = parseInt(year/100) + 1
    if(r < 20) return r + 'th'; 
    switch(r%10){

        case 1: return r + 'st';
        case 2: return r + 'nd';
        case 3: return r + 'rd';
        default: return r + 'th';
    }
} 
```

### 题解二：

```
 function whatCentury(year)
{
  var century = Math.ceil(year/100); 
  return century + (century < 20 ? 'th' : ['th', 'st', 'nd', 'rd'][century % 10] || 'th');
} 
```