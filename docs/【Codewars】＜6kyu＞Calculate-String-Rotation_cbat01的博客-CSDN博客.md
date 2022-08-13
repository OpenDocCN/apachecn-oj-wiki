<!--yml
category: codewars
date: 2022-08-13 11:41:42
-->

# 【Codewars】＜6kyu＞Calculate String Rotation_cbat01的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_36270908/article/details/111595296?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-20-111595296-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_36270908/article/details/111595296?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-20-111595296-null-null.142^v40^control,185^v2^control&utm_term=codewars)

### 一、题目：

> Write a function that receives two strings and returns n, where n is equal to the number of characters we should shift the first string > forward to match the second.
> 
> For instance, take the strings “fatigue” and “tiguefa”. In this case, the first string has been rotated 5 characters forward to produce the second string, so 5 would be returned.
> 
> If the second string isn’t a valid rotation of the first string, the method returns -1.
> 这道题要我们编写一个接收两个字符串并返回n的函数，其中n等于我们应该将第一个字符串前移（右移）以匹配第二个字符串的字符数。
> 如果第二个字符串不是第一个字符串前移（右移）可以得到，则该方法返回-1。

### 二、例子：

```
"coffee", "eecoff" => 2
"eecoff", "coffee" => 4
"moose", "Moose" => -1
"isn't", "'tisn" => 2
"Esham", "Esham" => 0
"dog", "god" => -1 
```

### 三、题解一：

```
function shiftedDiff(first,second){
    for(let i=0;i<first.length;i++){
        if(first.substr(first.length-i,i) + first.substr(0, first.length-i) == second) return i;
    }
    return -1;
} 
```

### 四、题解二：（Best Practices）

```
function shiftedDiff(first, second) {
  if (first.length != second.length) return -1
  return (second + second).indexOf(first)
} 
```