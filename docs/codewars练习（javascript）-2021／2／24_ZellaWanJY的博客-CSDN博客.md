<!--yml
category: codewars
date: 2022-08-13 11:34:43
-->

# codewars练习（javascript）-2021/2/24_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/114010417?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-114010417.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/114010417?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-114010417.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/2/24

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Grasshopper - Grade book】

完成该函数，以便它找到传递给它的三个分数的**平均值**，并返回与该成绩相关的字母值。

**<mark>example</mark>**：

```
Numerical Score	Letter Grade
90 <= score <= 100	'A'
80 <= score < 90	'B'
70 <= score < 80	'C'
60 <= score < 70	'D'
0 <= score < 60	'F' 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function getGrade (s1, s2, s3) {
            console.log(s1,s2,s3)
            var score = (s1 + s2 + s3)/3
            if(score<60 && score >=0)return 'F';
            else if(score<70 && score >=60 )return 'D'
            else if(score<80 && score >=70 )return 'C'
            else if(score<90 && score >=80 )return 'B'
            else return 'A'
        }

        console.log(getGrade(95,90,93));
        console.log(getGrade(44,55,52)); </script> 
```

#### 【2】<8kyu>【Stringy Strings】

write me a function `stringy` that takes a `size` and returns a `string` of alternating `'1s'` and `'0s'`.

**<mark>example</mark>**：

```
the string should start with a 1.

a string with size 6 should return :'101010'.

with size 4 should return : '1010'.

with size 12 should return : '101010101010'.

The size will always be positive and will only use whole numbers. 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function stringy(size) {
            var str='';
            for( var i=1; i<=size; i++ )
                str+=i%2;
            return str;
        }

        console.log(stringy(1))
        console.log(stringy(6));
        console.log(stringy(4)); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>