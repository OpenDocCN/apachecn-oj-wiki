<!--yml
category: codewars
date: 2022-08-13 11:37:08
-->

# 【codewars-13】和为奇数还是偶数 ?_Salted_Sun的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42338512/article/details/123774812?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-21-123774812-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_42338512/article/details/123774812?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-21-123774812-null-null.142^v40^control,185^v2^control&utm_term=codewars)

Task:
Given a list of integers, determine whether the sum of its elements is odd or even.

Give your answer as a string matching “odd” or “even”.

If the input array is empty consider it as: [0] (array with a zero).

Examples:

```
Input: [0]
Output: "even"

Input: [0, 1, 4]
Output: "odd"

Input: [0, -1, -5]
Output: "even" 
```

**要点**

*   用了刚学过的`std::accumulate` 完成求和.

```
#include <string>
#include <vector>
#include <numeric>

std::string odd_or_even(const std::vector<int> &arr)
{
 auto res =  std::accumulate(arr.begin() , arr.end(), 0, [](int a ,int b){return a+b;}) ;

  return res%2 != 0 ? "odd" : "even";  
} 
```