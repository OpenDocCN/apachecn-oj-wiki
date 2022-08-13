<!--yml
category: codewars
date: 2022-08-13 11:39:59
-->

# codewars (6 kyu) Decode the Morse code_lhapy的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41746553/article/details/103640307?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-7-103640307-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_41746553/article/details/103640307?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-7-103640307-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 一、题目简介

## 1\. Description:

> In this kata you have to write a simple Morse code decoder. While the Morse code is now mostly superceded by voice and digital data communication channels, it still has its use in some applications around the world.
> The Morse code encodes every character as a sequence of “dots” and “dashes”. The Morse code is case-insensitive, traditionally capital letters are used. When the message is written in Morse code, a single space is used to separate the character codes and 3 spaces are used to separate words. For example, the message <mark>HEY JUDE</mark> in Morse code is <mark>···· · −·−− ·−−− ··− −·· ·</mark>.

> **NOTE**: Extra spaces before or after the code have no meaning and should be ignored.

> *Your task* is to implement a function that would take the morse code as input and return a decoded human-readable string.

## 2\. 个人理解

**本题就是让我们实现一个莫斯密码的解密函数。
输入：string morseCode
输出：string plainText**

# 二、代码分析

## 1\. 代码实现

```
std::string decodeMorse(std::string morseCode) {

    morseCode.erase(0, morseCode.find_first_not_of(" "));
    morseCode.erase(morseCode.find_last_not_of(" ") + 1);

    std::string decoded;

    std::string letter_digit = "";
    std::string space = "";

    int flag; 
    int old_flag = 1;

    for(auto p : morseCode)
    {
      if( p == '.' || p == '-')
      {
        letter_digit += p;
        flag = 0;

      }
      else if( p == ' ')
      {
        space += p;
        flag = 1;
      }

      if(old_flag != flag)
      {
        if(old_flag == 0)
        {
          decoded += MORSE_CODE[ letter_digit ];
          letter_digit = "";
        }
        else if(old_flag == 1 )
        {
          if( space == "   " )
            decoded += " ";
          space = "";
        }
      }

      old_flag = flag;
    }

    if(flag == 0)
      decoded += MORSE_CODE[ letter_digit ];

    return decoded;
} 
```

## 2\. 实现思路

**设置两个缓存器 letter_digit、space**
       **letter_digit：缓存收到的单词(Words)**
       **space：缓存收到的空格**

**设置两个标记位flag、old_flag**
       **flag：当前改变的是 letter_digit 还是 space**
       **old_flag：记录前一步的 flag**

**然后，逐字符的读取 morseCode ，利用 flag 和 old_flag 控制输出字母数字还是空格。**

*补充：看别人有用正则表达式进行匹配的。*

**link:** [Best Solutions](https://www.codewars.com/kata/decode-the-morse-code/solutions/cpp/all/best_practice)

## 3\. 收获

**（1）C++去除字符串首部尾部的空格**
**（2）C++中,双引号 “a” 是 const char * 类型的。所以，进行比较时，需要使用单引号 'a’**

* * *