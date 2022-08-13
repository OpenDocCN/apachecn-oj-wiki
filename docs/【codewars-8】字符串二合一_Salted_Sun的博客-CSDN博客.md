<!--yml
category: codewars
date: 2022-08-13 11:40:54
-->

# 【codewars-8】字符串二合一_Salted_Sun的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42338512/article/details/123731676?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-2-123731676-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_42338512/article/details/123731676?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-2-123731676-null-null.142^v40^control,185^v2^control&utm_term=codewars)

Take 2 strings s1 and s2 including only letters from ato z. Return a new sorted string, the longest possible, containing distinct letters - each taken only once - coming from s1 or s2.
用两个字符串中的字符组成无重复字符且升序排列的字符串

```
Examples:
a = "xyaabbbccccdefww"
b = "xxxxyyyyabklmopq"
longest(a, b) -> "abcdefklmopqwxy"

a = "abcdefghijklmnopqrstuvwxyz"
longest(a, a) -> "abcdefghijklmnopqrstuvwxyz" 
```

**要点**

*   将两个字符串放入set中进行去重. 然后用set初始化一个string中进行排序

```
#include <set>

class TwoToOne
{
public:
    static std::string longest(const std::string &s1, const std::string &s2){

      std::string sum = s1 == s2? s1 : s1+s2 ;
      std::set<char> chars{sum.begin() , sum.end()};
      std::string res{chars.begin() , chars.end()};

      std::sort(res.begin() , res.end()) ;
      return  res;

    }
}; 
```