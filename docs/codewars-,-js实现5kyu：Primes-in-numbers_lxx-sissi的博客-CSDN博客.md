<!--yml
category: codewars
date: 2022-08-13 11:45:33
-->

# codewars , js实现5kyu:Primes in numbers_lxx-sissi的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_35438535/article/details/106208063?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-106208063.nonecase](https://blog.csdn.net/sinat_35438535/article/details/106208063?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-106208063.nonecase)

# 题目描述

该kata的链接地址: [link](https://www.csdn.net/).

Given a positive number n > 1 find the prime factor decomposition of n. The result will be a string with the following form :

“(p1**n1)(p2**n2)…(pk**nk)”
with the p(i) in increasing order and n(i) empty if n(i) is 1.

# Example

```
Example: n = 86240 should return "(2**5)(5)(7**2)(11)"
Test.assertEquals(primeFactors(7775460),"(2**2)(3**3)(5)(7)(11**2)(17)") 
```

# 代码实现

## 我完成代码

```
function primeFactors(n){

            var newArr = [],obj = {},str = '';
            cal(n);
            function cal(n){
              if(n > 1){
                for(var i = 2;i <= n ;i++){
                  if(n%i == 0){   
                    newArr.push(i);
                    cal(n/i);
                    return true; 
                  }
                }
              }
              else{
                return true;
              }
            }
            newArr.map(function(x){
              obj[x] ? obj[x]++ : obj[x] = 1;
            });
            for (var item in obj) {
              obj[item] == 1 && (str += '('+ item +')')
              obj[item] > 1 && (str += '('+item +'**'+ obj[item]+')')
            }
            return str;
        } 
```

# 解题思路

# 难点