<!--yml
category: codewars
date: 2022-08-13 11:46:50
-->

# codewars练习（javascript）-2021/3/16_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/114867129?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-114867129.nonecase](https://blog.csdn.net/FemaleHacker/article/details/114867129?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-114867129.nonecase)

## codewars-js练习

### 2021/3/16

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Billiards pyramid】

**<mark>example</mark>**：

```
 *
   *   *
 *   *    *

pyramid(1) == 1

pyramid(3) == 2

pyramid(6) == 3

pyramid(10) == 4

pyramid(15) == 5 
```

**<mark>思路</mark>**

假设 pyramid(balls) == n；则满足 n 2 + n 2 = b a l l s \frac{n^2+n}{2}= balls 2n2+n​=balls，因此现在反求出n即可。

<mark>**solution**</mark>

```
<script type="text/javascript"> function pyramid(balls) {

        var deta = 1 + 8*balls;
        var result = (-1+Math.sqrt(deta,2))/2;
        return Math.floor(result);
    }

    console.log(pyramid(21));
    console.log(pyramid(10)); </script> 
```

#### 【2】<8kyu>【Twice as old】

Your function takes two arguments:

1.  current father’s age (years)
2.  current age of his son (years)

Сalculate how many years ago the father was twice as old as his son (or in how many years he will be twice as old).

**<mark>example</mark>**：

```
(36,7)
(55,30)
(29,0) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function twiceAsOld(dadYearsOld, sonYearsOld) {

        return Math.abs(sonYearsOld * 2 - dadYearsOld)
    }

    console.log(twiceAsOld(36,7));
    console.log(twiceAsOld(42,21));
    console.log(twiceAsOld(29,0));
    console.log(twiceAsOld(55,30)); </script> 
```