<!--yml
category: codewars
date: 2022-08-13 11:43:28
-->

# 记codewars一道题 Reverse words 解题过程_指针的值是地址的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_40007143/article/details/104134301?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-104134301.nonecase](https://blog.csdn.net/weixin_40007143/article/details/104134301?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-104134301.nonecase)

## problem

Complete the function that accepts a string parameter, and reverses each word in the string. All spaces in the string should be retained.
输入一个字符串，逆序每一个单词，所有的空格都需要保留。

## Example

“This is an example!” ->“sihT si na !elpmaxe”
“double spaces” -> “elbuod secaps”

## Solve

##### 1.0版本

```
#include <sstream>
#include <iostream>
using namespace std;
string reverse_words(string str)
{
    stringstream ss(str);
    string a;
    string b;
    while (ss >> b)
    {
        for (int i1 = 0; i1 < b.length() / 2; i1++)
        {
            char te;
            te = b[b.length() - 1 - i1];
            b[b.length() - 1 - i1] = b[i1];
            b[i1] = te;
        }
        a = a + b;
        a = a + " ";
    }
    a.erase(a.end()-1);
    return a;
} 
```

失败，原因是未考虑到多个空格的情况。

##### 2.0版本

```
#include <string.h>
#include <string>
#include <iostream>
using namespace std;
#pragma warning(disable:4996)
string reverse_words(string str)
{
    char *str1 = (char*)str.data();
    char *c = (char*)" ";
    string a;
    char* b;
    b = strtok(str1, c);
    while (b != NULL) {
        for (int i1 = 0; i1 < strlen(b) / 2; i1++)
        {
            char te;
            te = b[strlen(b) - 1 - i1];
            b[strlen(b) - 1 - i1] = b[i1];
            b[i1] = te;
        }
        a = a + b;
        a = a + " ";
        b = strtok(NULL, c);
    }
    a.erase(a.end() - 1);   
    return a;
} 
```

换了个函数来实现，还是不行，本质上还是因为没有充分理解strtok()这个函数，这个函数在遇到两个空格时，依然不能达到题目要求。

##### 3.0版本

```
#include <string>
#include <iostream>
using namespace std;
#pragma warning(disable:4996)
string reverse_words(string str)
{
    int i = 0;
    int j = -1;
    while (j!=str.length()-1) {
        for (int i1 = j+1; i1 < str.length(); i1++)
        {
            if (str[i1] != ' ') {
                i = i1; break;
            }
        }
        for (int j1 = i; j1 < str.length()+1; j1++)
        {
            if ((str[j1] == ' ') || (j1 == str.length())) {
                j = j1 - 1; break;
            }
        }
        for (int i2 = 0; i2 <= (j-i) / 2; i2++)
        {
            char te;
            te = str[j- i2];
            str[j- i2] = str[i+i2];
            str[i+i2] = te;
        }
    }
    return str;
} 
```

这次的代码可以满足题目要求了，但是时间复杂度过高。没过最终的attemp.
然后参考了别人的代码，真的是简单！之后得出了4.0版本。

##### 4.0版本

```
string reverse_words(string str)
{
    string out;  
    string a_word;
    for (char c : str) {
        if (c != ' ') {  
            a_word = c + a_word;
        }
        if (c == ' ') {  
            out = out + a_word;
            a_word = "";  
            out = out + " ";  
        }
    }
    out = out + a_word;
    return out;
} 
```

这思路不能在简单了。真的是绝了。太强了。
这就是这次做题的思路过程。
谢谢阅读！