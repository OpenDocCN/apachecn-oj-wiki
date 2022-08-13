<!--yml
category: codewars
date: 2022-08-13 11:37:52
-->

# 【codewars-17】统计字符的出现次数_Salted_Sun的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42338512/article/details/123821154?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-10-123821154-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_42338512/article/details/123821154?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-10-123821154-null-null.142^v40^control,185^v2^control&utm_term=codewars)

The main idea is to count all the occurring characters in a string. If you have a string like aba, then the result should be {‘a’: 2, ‘b’: 1}.

What if the string is empty? Then the result should be empty object literal, {}.

```
#include <map>
#include <string>

std::map<char, unsigned> count(const std::string& str ) {
  if(str == "")  return {};
  std::map<char, unsigned> res{};
  for(auto &e : str){
    res[e] += 1;
  }
  return res;
} 
```