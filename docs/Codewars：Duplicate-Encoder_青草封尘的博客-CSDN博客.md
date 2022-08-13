<!--yml
category: codewars
date: 2022-08-13 11:48:37
-->

# Codewars:Duplicate Encoder_青草封尘的博客-CSDN博客

> 来源：[https://blog.csdn.net/w1961557599/article/details/100671072?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-100671072.nonecase](https://blog.csdn.net/w1961557599/article/details/100671072?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-100671072.nonecase)

要求：

> The goal of this exercise is to convert a string to a new string where each character in the new string is “(” if that character appears only once in the original string, or “)” if that character appears more than once in the original string. Ignore capitalization when determining if a character is a duplicate.**

> Examples:
> “din” => “(((”
> “recede” => “()()()”
> “Success” => “)())())”
> “(( @” => “))((”

思路：先把每个大写字符转化成小写，在统计数目

```
char *DuplicateEncoder(char *s)
{
  int dup[256];        // 存储数字为字符个数
  char* ret;           //返回的字符数组
  ret=malloc((strlen(s)+1)*sizeof(char));

  for(int i=0; i<256; i++) dup[i]=0;

  for(int i=0; i<strlen(s); i++) dup[tolower(s[i])]++;

  for(int i=0; i<strlen(s); i++)
  {
    if(dup[tolower(s[i])]>1) ret[i]=')';
    else ret[i]='(';
  }
  ret[strlen(s)]='\0';

  return  ret;
} 
```

代码的可取之处在于*dup[tolower(s[i])]++*；
这是在看了别人的代码基础上理解的，让人不禁感叹这就是灵活多变的c语言之美和代码之妙啊
tolower可将字符串中的大写字母转化为小写；
toupper可将字符串中的小写字母转化为大写；