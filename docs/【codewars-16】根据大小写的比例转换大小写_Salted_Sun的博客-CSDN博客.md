<!--yml
category: codewars
date: 2022-08-13 11:38:29
-->

# 【codewars-16】根据大小写的比例转换大小写_Salted_Sun的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42338512/article/details/123820240?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-29-123820240-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_42338512/article/details/123820240?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-29-123820240-null-null.142^v40^control,185^v2^control&utm_term=codewars)

In this Kata, you will be given a string that may have mixed uppercase and lowercase letters and your task is to convert that string to either lowercase only or uppercase only based on:

make as few changes as possible.
if the string contains equal number of uppercase and lowercase letters, convert the string to lowercase.
For example:

```
solve("coDe") = "code". Lowercase characters > uppercase. Change only the "D" to lowercase.
solve("CODe") = "CODE". Uppercase characters > lowecase. Change only the "e" to uppercase.
solve("coDE") = "code". Upper == lowercase. Change all to lowercase. 
```

**要点**

*   `count_if` 对大写字母进行计数
*   `::islower/::isupper` 用于判断大小写字母
*   `transform`进行大小写转换
*   注意和size_t类型的比较

```
#include <string>

std::string solve(const std::string& str){

  size_t upper_count{};
upper_count =  std::count_if(str.begin() , str.end(), []( char ch){
    return  ch <=  'Z';
  }) ;
 std::string res{str};
 if(upper_count > str.size() - upper_count){
 std::transform(res.begin(), res.end() ,res.begin(), ::toupper ) ;

 }else {

 std::transform(res.begin() , res.end() , res.begin(), ::tolower);
 }
 return res;

} 
```

**更精简的解法**

```
#include <string>

std::string solve(const std::string& str){
  std::string res{str};

  size_t upper_count = std::count_if(str.begin(), str.end() , ::isupper);
  auto func = upper_count > str.size() - upper_count ? (::toupper) :(::tolower) ;
  std::transform(res.begin() , res.end(), res.begin(), func);
  return res;
} 
```