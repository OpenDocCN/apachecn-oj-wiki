<!--yml
category: codewars
date: 2022-08-13 11:36:46
-->

# codewars练习（javascript）-2021/3/7_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/114478781?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-114478781.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/114478781?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-114478781.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/3/7

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Convert a Number to a String!】

<mark>**solution**</mark>

```
<script type="text/javascript"> function numberToString(num) {

            return num.toString();
        }

        console.log(numberToString(67)); </script> 
```

#### 【2】<8kyu>【Grasshopper - Personalized Message】

<mark>**solution**</mark>

```
<script type="text/javascript"> function greet (name, owner) {
            if(name == owner)return 'Hello boss'
            return 'Hello guest'
        }

        console.log(greet('Daniel', 'Daniel'));
        console.log(greet('Greg', 'Daniel')); </script> 
```

#### 【3】<6kyu>【1/n- Cycle】

**<mark>example</mark>**：

```
cycle(5) = -1
cycle(13) = 6 -> 0.076923 076923 0769
cycle(21) = 6 -> 0.047619 047619 0476
cycle(27) = 3 -> 0.037 037 037 037 0370
cycle(33) = 2 -> 0.03 03 03 03 03 03 03 03
cycle(37) = 3 -> 0.027 027 027 027 027 0
cycle(94) = -1 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function cycle(n) {
            console.log(n)
            if(n%2 ==0 || n%5 == 0)return -1;
            var i =0;
            var val = 1;
            while(++i){
                val = val * 10 % n;
                if(val == 1) return i;
            }
        }

        console.log(cycle(33));
        console.log(cycle(18118));
        console.log(cycle(69));
        console.log(cycle(197)); </script> 
```