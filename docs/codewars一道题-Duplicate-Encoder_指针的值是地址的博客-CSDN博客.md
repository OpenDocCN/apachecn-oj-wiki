<!--yml
category: codewars
date: 2022-08-13 11:48:46
-->

# codewars一道题 Duplicate Encoder_指针的值是地址的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_40007143/article/details/104100520?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-104100520.nonecase](https://blog.csdn.net/weixin_40007143/article/details/104100520?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-104100520.nonecase)

## problem

The goal of this exercise is to convert a string to a new string where each character in the new string is “(” if that character appears only once in the original string, or “)” if that character appears more than once in the original string. Ignore capitalization when determining if a character is a duplicate.
就是说给定一个字符串，遍历每个元素，如果这个元素出现的次数超过一次，输出")".如果这个元素的出现的次数就一次，输出"("。忽略字母的大小写。

## Solution

```
#include <map>
#include <string>
#include <cctype>
using namespace std;
string duplicate_encoder(const string& word){
  string a;
  string word1=word;
  map<char,int>b;
  for(auto x:word1) b[tolower(x)]++;    
  for(auto x:word1) a+=(b[tolower(x)]>1)?")":"(";
  return a;
} 
```

这代码是看的别人的，不得不说，这代码对库函数的理解很透彻。代码很简洁！