<!--yml
category: codewars
date: 2022-08-13 11:36:57
-->

# 【codewars-14】选择性转换大写_Salted_Sun的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42338512/article/details/123775528?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-15-123775528-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_42338512/article/details/123775528?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-15-123775528-null-null.142^v40^control,185^v2^control&utm_term=codewars)

Given a string, capitalize the letters that occupy even indexes and odd indexes separately, and return as shown below. Index 0 will be considered even.

For example, capitalize(“abcdef”) = [‘AbCdEf’, ‘aBcDeF’]. See test cases for more examples.

The input will be a lowercase string with no spaces.

**要点**

*   主要思路是用`std::transform`进行大写转换, 因为需要使用字符的位置信息, 因此需要让`lambda`表达式对外部的`index`进行绑定.
*   `std::transform`的输出容器必须要保证其空间 `>=` 输入容器的空间, 否则输出容器中的结果将不完整. 在这里用`resize()`来保证有足够的空间, 否则没有输出结果

```
#include <string>
#include <utility>

std::pair<std::string, std::string> capitalize(const std::string &s)
{
  std::string first{};
  std::string second{};

  first.resize(s.size());  
  second.resize(s.size());

  int index{0};
  std::transform(s.begin(),s.end() , first.begin(), [&index](char ch){ return  index++%2==0? ::toupper(ch) : ch ;  } );

  index = 0;
  std::transform(s.begin(),s.end() ,second.begin(), [&index](char ch){ return   index++ %2!=0? ::toupper(ch) : ch ; } );

  return {first, second};
} 
```