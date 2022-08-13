<!--yml
category: codewars
date: 2022-08-13 11:40:17
-->

# codewars练习（javascript）-2021/2/27_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/114161375?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-13-114161375-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/114161375?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-13-114161375-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/2/27

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Complete Series】

You are given an array of non-negative integers, your task is to complete the series from 0 to the highest number in the array.

If the numbers in the sequence provided are not in order you should order them, but if a value repeats, then you must return a sequence with only one item, and the value of that item must be 0.

**<mark>example</mark>**：

```
inputs        outputs
[0,1]   ->    [0,1]
[1,4,6] ->    [0,1,2,3,4,5,6]
[3,4,5] ->    [0,1,2,3,4,5]
[0,1,0] ->    [0] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function completeSeries(arr) {

            if((new Set(arr)).size != arr.length) return [0];
            let max = Math.max(...arr)
            let result = [];
            for(let i=0;i<=max;i++){result.push(i)}
            return result;
        }

        console.log(completeSeries([0,1]));
        console.log(completeSeries([1,4,6]));
        console.log(completeSeries([1,4,4,6])); </script> 
```

**<mark>知识点</mark>**

js判断数组是否存在重复元素 --> **es6中的set方法即可**

```
var arr = [1,2,3,4,5,2,3];
if((new Set(arr)).size != arr.length){
    alert("数组有重复值")
} 
```

#### 【2】<6kyu>【Complete Fibonacci Series】

The function ‘fibonacci’ should return an array of fibonacci numbers. The function takes a number as an argument to decide how many no. of elements to produce. If the argument is less than or equal to 0 then return empty array

**<mark>example</mark>**：

```
2
5
13
-5 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function fibonacci(n) {

            if(n<=0)return [];
            var result = [];
            var res1 = 1;
            var res2 = 1;
            var sum = res2;
            if(n == 1)result.push(0);
            else if(n == 2) result = [0,1];
            else if(n == 3) result = [0,1,1];
            else if(n>3){
                result = [0,1,1]
                for(var i = 1;i < n-2;i ++){
                    sum = res1 + res2;
                    res1 = res2;
                    res2 = sum;

                    result.push(sum)

                }
            }
            return result;
        }

        console.log(fibonacci(2));
        console.log(fibonacci(5));
        console.log(fibonacci(13));
        console.log(fibonacci(-5)); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>

周末愉快