<!--yml
category: codewars
date: 2022-08-13 11:40:51
-->

# 【Codewars】＜4kyu＞Sum Strings as Numbers_cbat01的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_36270908/article/details/111994142?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-30-111994142-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_36270908/article/details/111994142?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-30-111994142-null-null.142^v40^control,185^v2^control&utm_term=codewars)

![](img/c0e0976231a3018381df3d35cf8dbfe4.png)

## 题目

**＜4kyu＞Sum Strings as Numbers**

> Given the string representations of two integers, return the string representation of the sum of those integers.
> A string representation of an integer will contain no characters besides the ten numerals “0” to “9”.
> 
> **给定两个整数的字符串表示形式，返回这些整数之和的字符串表示形式。**
> （注：这两个字符串将不包含除“0”到“9”之外的任何字符。）

## 例子

```
sumStrings('1','2') 
sumStrings('','5') 
sumStrings('001','5') 
sumStrings('50095301248058391139327916261','81055900096023504197206408605') 
```

## 题解一

```
 function sumStrings(a,b) {
    var result = '';
    var remainder = 0;
    if(a.length < b.length) {
        var c = a;
        a = b;
        b = c;
    }
    for(let i=1;i<=a.length;i++){

        var sum =  (a.length-(i-1)>0 ? parseInt(a.substr(a.length-i,1)) : 0) + (b.length-(i-1)>0 ? parseInt(b.substr(b.length-i,1)) : 0)  + remainder;

        result = sum%10 + result

        remainder = parseInt(sum/10)

        if(remainder > 0 && i == a.length) result = remainder + result;
    }
    return result.replace(/\b(0+)/gi,""); 
} 
```

## 题解二（Best Practices）

```
 function sumStrings(a, b) {
    var res = '', c = 0;
    a = a.split('');
    b = b.split('');
    while (a.length || b.length || c) {
      c += ~~a.pop() + ~~b.pop();
      res = c % 10 + res;
      c = c > 9;
    }
    return res.replace(/^0+/, '');
} 
```

小伙伴们有其它更好的解法，欢迎评论区提出交流~