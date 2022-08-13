<!--yml
category: codewars
date: 2022-08-13 11:40:43
-->

# 【Codewars】＜7kyu＞Char Code Calculation_cbat01的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_36270908/article/details/111667835?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-27-111667835-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_36270908/article/details/111667835?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-27-111667835-null-null.142^v40^control,185^v2^control&utm_term=codewars)

### 题目：

```
Given a string, turn each character into its ASCII character code and join them together to create a number - let's call this number total1:
'ABC' --> 'A' = 65, 'B' = 66, 'C' = 67 --> 656667

Then replace any incidence of the number 7 with the number 1, and call this number 'total2':

total1 = 656667
              ^
total2 = 656661
              ^
Then return the difference between the sum of the digits in total1 and total2:
  (6 + 5 + 6 + 6 + 6 + 7)
- (6 + 5 + 6 + 6 + 6 + 1)
-------------------------
                       6

题目翻译：给定一个字符串，将字符串的每一个字母转成ASCII码，然后拼接到一起，得到第一个数字`total1`，将`total1`中的数字`7`替换成数字`1`，得到第二个数字`total2`,最后返回total1中各位数字之和与total2中的各位数字之和的差 
```

### 题解一：

```
 function calc(x){
    var xA = ''
    for(let i=0;i<x.length;i++){
        xA += x.substr(i,1).charCodeAt()
    }
    return (xA.match(/7/g) || []).length * 6;
} 
```

### 题解二：

```
 const calc=x=>(x.replace(/./g,x=>x.charCodeAt()).match(/7/g)||[]).length*6 
```