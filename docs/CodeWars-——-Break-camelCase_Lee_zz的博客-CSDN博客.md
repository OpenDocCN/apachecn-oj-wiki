<!--yml
category: codewars
date: 2022-08-13 11:36:16
-->

# CodeWars —— Break camelCase_Lee_zz的博客-CSDN博客

> 来源：[https://blog.csdn.net/Lee_zz/article/details/116753773?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-116753773-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/Lee_zz/article/details/116753773?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-116753773-null-null.142^v40^control,185^v2^control&utm_term=codewars)

Complete the solution so that the function will break up camel casing, using a space between words.

## Example

```
"camelCasing"  =>  "camel Casing"
"identifier"   =>  "identifier"
""             =>  "" 
```

**我的**

```
function solution(string) {
    return string.split('').map(i=>(
      (i.charCodeAt(0) >= 65 && i.charCodeAt(0) <= 90) ? ' ' + i : i
    )).join('')
} 
```

这里除了比较unicode码范围以外，也可以 === 判断是否与 toUpperCase() 值相同

**别人的**

```
function solution(string) {
  return(string.replace(/([A-Z])/g, ' $1'));
} 
```