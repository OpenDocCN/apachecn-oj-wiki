<!--yml
category: codewars
date: 2022-08-13 11:45:59
-->

# [Codewars]-Roman Numerals Encoder___Charming__的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41882147/article/details/79672582?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-79672582.nonecase](https://blog.csdn.net/qq_41882147/article/details/79672582?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-79672582.nonecase)

### [Codewars]-Roman Numerals Encoder

#### 题目：

| symbol | value |
| --- | --- |
| I | 1 |
| V | 5 |
| X | 10 |
| L | 50 |
| C | 100 |
| D | 500 |
| M | 1000 |

- ps：2000 -> MM，8000 -> MMMMMMMM

#### 思路：

*   按照题目，把数字分成几千几百几十很好转换，唯一问题是代码长不美观。

### 解答：

```
function solution(number){

var  roman = {M:1000,CM:900, D:500,CD:400,C:100,XC:90,L:50,XL:40,X:10,IX:9,V:5,IV:4,I:1 }

var ans = '';
while(number>0){
    for(a in roman){ 
        if(roman[a]<=number){ ans += a; number-=roman[a]; break;}

    }
}
return ans;
}
```