<!--yml
category: codewars
date: 2022-08-13 11:36:24
-->

# codewars练习（javascript）-2021/3/14_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/114776911?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-4-114776911-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/114776911?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-4-114776911-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/3/14

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<6kyu>【Cumulative Triangle】

**<mark>example</mark>**：

```
 1
   2 3
  4 5 6
 7 8 9 10
...
Given N, return the sum of all numbers on the Nth Row

2
3 
```

**<mark>思路</mark>**

第n行首字母就是 n ( n − 1 ) 2 + 1 \frac{n(n-1)}{2} + 1 2n(n−1)​+1

<mark>**solution**</mark>

```
<script type="text/javascript"> function cumulativeTriangle(n) {
        console.log(n)
        var first = (n*(n-1))/2 + 1;
        var last = first + (n-1);
        var sum = 0;
        for(var i=first;i<=last;i++){
            sum +=i;
        }
        return sum;
    }

    console.log(cumulativeTriangle(2));
    console.log(cumulativeTriangle(3)); </script> 
```

#### 【2】<6kyu>【Follow that Spy】

**<mark>example</mark>**：

```
[ [USA, BRA], [JPN, PHL], [BRA, UAE], [UAE, JPN] ] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function findRoutes(routes) {
        console.log(routes);
        var arr=routes[0];
        for(var i=0;i<routes.length;i++){
            for(var j=1;j<routes.length;j++){
                if(routes[j][0] == arr[arr.length-1]){
                    arr.push(routes[j][1])
                }else if(routes[j][1] == arr[0]){
                    arr.unshift(routes[j][0]);
                }
            }
        }
        return arr.join(', ');
    }

    console.log(findRoutes([["MNL", "TAG"], ["CEB", "TAC"], ["TAG", "CEB"], ["TAC", "BOR"]]));
    console.log(findRoutes([["USA", "BRA"], ["JPN", "PHL"], ["BRA", "UAE"], ["UAE", "JPN"]])); </script> 
```