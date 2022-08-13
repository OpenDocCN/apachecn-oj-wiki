<!--yml
category: codewars
date: 2022-08-13 11:37:04
-->

# codewars练习（javascript）-2021/3/6_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/114453869?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-19-114453869-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/114453869?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-19-114453869-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/3/6

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【You Can’t Code Under Pressure #1】

Code as fast as you can! You need to double the integer and return it.

**<mark>example</mark>**：

```
2 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function doubleInteger(i) {
            console.log(i)
            return i*2

        } 

        console.log(2); </script> 
```

#### 【2】<8kyu>【Beginner Series #4 Cockroach】

The cockroach is one of the fastest insects. Write a function which takes its speed in km per hour and returns it in cm per second, rounded down to the integer (= floored).

**它的速度是千米每小时，返回的是厘米每秒，**

**<mark>example</mark>**：

```
cockroachSpeed(1.08) == 30 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function cockroachSpeed(s) {

            return parseInt(s * (1/36)*1000)
        } 

        console.log(cockroachSpeed(1.08));
        console.log(cockroachSpeed(1.09));
        console.log(cockroachSpeed(0)); </script> 
```

#### 【3】<8kyu>【Opposites Attract】

Timmy & Sarah think they are in love, but around where they live, they will only know once they pick a flower each. If one of the flowers has an even number of petals and the other has an odd number of petals it means they are in love.

Write a function that will take the number of petals of each flower and return true if they are in love and false if they aren’t.

**如果一朵花的花瓣数是偶数，另一朵花的花瓣数是奇数，这意味着他们相爱了。**

**<mark>example</mark>**：

```
(1,4) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function lovefunc(flower1, flower2){

            var bool1 = (flower1%2==0) && (flower2%2!=0)
            var bool2 = (flower2%2==0) && (flower1%2!=0)
            if(bool1 || bool2)return true;
            return false;
        } 

        console.log(lovefunc(1,4));
        console.log(lovefunc(2,2));
        console.log(lovefunc(0,1));
        console.log(lovefunc(0,0)); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>