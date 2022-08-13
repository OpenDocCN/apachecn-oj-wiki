<!--yml
category: codewars
date: 2022-08-13 11:37:20
-->

# CodeWars C++ Convert string to camel case【6 kyu】_memcpy0的博客-CSDN博客

> 来源：[https://blog.csdn.net/myRealization/article/details/105067169?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-28-105067169-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/myRealization/article/details/105067169?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-28-105067169-null-null.142^v40^control,185^v2^control&utm_term=codewars)

Complete the method/function so that it converts **dash/underscore** delimited words into **camel casing**. The first word within the output should be **capitalized** only if the original word was capitalized (known as **Upper Camel Case**, also often referred to as **Pascal case**).

Examples

```
to_camel_case("the-stealth-warrior") // returns "theStealthWarrior"

to_camel_case("The_Stealth_Warrior") // returns "TheStealthWarrior" 
```

题意：很简单的题目，本来以为会在一些测试点上面卡人，不过事实证明我想多了。就是把一串用 − - − 或者 _ \_ _ 隔开的单词的**首字母大写**，除了第一个单词的首字母不用处理。（做这个更多的是习惯英文环境吧）… 另外，Codewars上面的C++的测试环境，我一时半会还用不好…

代码：这里用到是迭代器删除。

```
std::string to_camel_case(std::string text) {
    if (text.size() == 0) return text;
    for (auto it = text.begin(); it != text.end(); ++it) {
      if (*it == '-' || *it == '_') {
        char &c = *(it + 1);
        c = toupper(c);
        text.erase(it);
      }
    }
    return text;
} 
```