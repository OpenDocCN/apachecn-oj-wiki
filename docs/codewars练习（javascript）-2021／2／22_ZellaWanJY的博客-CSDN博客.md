<!--yml
category: codewars
date: 2022-08-13 11:41:27
-->

# codewars练习（javascript）-2021/2/22_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113930068?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-13-113930068-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/113930068?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-13-113930068-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/2/22

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<6kyu>【Sums of Parts】

**<mark>example</mark>**：

```
Let us consider this example (array written in general format):

ls = [0, 1, 3, 6, 10]

Its following parts:

ls = [0, 1, 3, 6, 10]
ls = [1, 3, 6, 10]
ls = [3, 6, 10]
ls = [6, 10]
ls = [10]
ls = []
The corresponding sums are (put together in a list): [20, 20, 19, 16, 10, 0] 
```

<mark>**solution**</mark>

**1先应用了以下这种方法，不考虑时间复杂度，可以实现功能，但提示超时**

```
//超时
<script type="text/javascript"> function partsSums(ls) {

            var len = ls.length;
            var result = [];
            for(var j=0;j<len+1;j++){
                var sum = Sum(ls)
                ls.shift()

                result.push(sum)
            }
            return result;
        }
        function Sum(arr){
            var sum = 0
            for(var i=0;i<arr.length;i++){
                sum +=arr[i];
            }
            return sum;
        }		

        console.log(partsSums([]));
		console.log(partsSums([0, 1, 3, 6, 10])); </script> 
```

**2因此改进了这种方法，运用了reduce，但还是提醒超时**

```
//超时
<script type="text/javascript"> function partsSums(ls) {

            var len = ls.length;
            var result = [];
            for(var i=0;i<len+1;i++){
                let sum = ls.reduce((a, b) => {return a + b;},0);

                result.push(sum)
                ls.shift()
            }
            return result
        }

        console.log(partsSums([]));
		console.log(partsSums([0, 1, 3, 6, 10])); </script> 
```

**3 最后经过各种尝试，选择了这种。reduce map。终于提示成功**

*   首先先在数组中添加一个元素0；
*   计算出起始的总和sum；
*   每次提出一个元素，并用初始sum减去该元素，算出新的当前sum；
*   将所有sum和弄成数组返回；
*   end。

```
//最终正确答案
<script type="text/javascript"> function partsSums(ls) {
            ls.unshift(0);
            let sum = ls.reduce((a, b) => a + b, 0);
            return ls.map(v => sum = sum - v);
        }

        console.log(partsSums([]));
		console.log(partsSums([0, 1, 3, 6, 10])); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>