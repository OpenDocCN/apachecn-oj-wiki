<!--yml
category: codewars
date: 2022-08-13 11:40:19
-->

# 【codewars-19】斐波那契的变种问题_Salted_Sun的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42338512/article/details/123918696?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-14-123918696-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_42338512/article/details/123918696?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-14-123918696-null-null.142^v40^control,185^v2^control&utm_term=codewars)

Well met with Fibonacci bigger brother, AKA Tribonacci.

As the name may already reveal, it works basically like a Fibonacci, but summing the last 3 (instead of 2) numbers of the sequence to generate the next. And, worse part of it, regrettably I won’t get to hear non-native Italian speakers trying to pronounce it 😦

So, if we are to start our Tribonacci sequence with [1, 1, 1] as a starting input (AKA signature), we have this sequence:

[1, 1 ,1, 3, 5, 9, 17, 31, …]
But what if we started with [0, 0, 1] as a signature? As starting with [0, 1] instead of [1, 1] basically shifts the common Fibonacci sequence by once place, you may be tempted to think that we would get the same sequence shifted by 2 places, but that is not the case and we would get:

[0, 0, 1, 1, 2, 4, 7, 13, 24, …]
Well, you may have guessed it by now, but to be clear: you need to create a fibonacci function that given a signature array/list, returns the first n elements - signature included of the so seeded sequence.

Signature will always contain 3 numbers; n will always be a non-negative number; if n == 0, then return an empty array (except in C return NULL) and be ready for anything else which is not clearly specified 😉

**分析**
此题目和斐波那契类似, 输入是数组的前三个元素, 每个元素是前3个元素之和, 唯一麻烦的地方是要返回N个元素的数组. 麻烦之处在于可能要要求返回小于三个元素的数组.

**要点**

*   用`vector.erase(.begin() )` 实现vector的pop_front
*   `std::accumulate()` + 反向迭代器 实现总是对数组最后三个元素求和.

```
#include <algorithm>
#include <numeric>
#include <vector>
std::vector<int> tribonacci(std::vector<int> signature, int n)
{
  std::vector<int> result{};
  while(result.size()< static_cast<size_t >(n) ){
    if(signature.size() > 0)
    {
      result.push_back(signature.front());
      signature.erase(signature.begin()); 
    } 
    else 
    {
      result.push_back( std::accumulate(result.rbegin(), result.rbegin()+3, 0 , [](int a , int b){return a+b;} )); 

    }
  }
  return result;
} 
```