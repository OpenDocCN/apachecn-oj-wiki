<!--yml
category: codewars
date: 2022-08-13 11:42:09
-->

# Reverse or rotate?（C++CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105930764?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-105930764-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/coolsunxu/article/details/105930764?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-105930764-null-null.142^v40^control,185^v2^control&utm_term=codewars)

解题思路：

（1）使用substr截取字符串，使用reverse颠倒字符串，使用“原地算法”移动字符串

```
#include <string>
#include <algorithm>

using std::string;
using std::reverse;

class RevRot {
public:
    static string revRot(const string &strng, unsigned int sz) {
        int len = strng.length();
        if(sz<=0||len==0||sz>len) return "";
        int chunk = len/sz,temp;
        string s,str="";
        for(int i=0;i<chunk;i++){
            s = strng.substr(i*sz,sz);
            if(judge(s)) reverse(s.begin(),s.end()),str+=s;
            else rotate(s),str+=s;
        }
        return str;
    }

    static void rotate(string &s) { //原地算法
        char c = s[0];
        for(int i=0;i<=s.length()-2;i++) {
            s[i] = s[i+1];
        }
        s[s.length()-1]=c;
    }

    static bool judge(string &s) {
        int sum = 0;
        for(auto w:s) sum+=(w-'0')*(w-'0')*(w-'0');
        return sum%2==0;
    }

};
```

（2）还可以使用递归，代码来自[https://www.codewars.com/kata/56b5afb4ed1f6d5fb0000991/solutions/cpp](https://www.codewars.com/kata/56b5afb4ed1f6d5fb0000991/solutions/cpp)

```
#include <string>
#include <algorithm>

class RevRot
{
public:
    static std::string revRot(const std::string &strng, unsigned int sz){
      if(sz <= 0 || strng.empty() || sz > strng.length())
        return "";
      std::string x = strng.substr(0,sz);
      bool p = true;
      for(const char& c : x)
        if(c % 2 == 1) // '0' == 48, so 'digit' is even iff digit is even 
          p = !p;
      if(p){
        std::reverse(x.begin(),x.end());
        return x + revRot(strng.substr(sz),sz);
      }
      x += x[0];
      return x.substr(1) + revRot(strng.substr(sz),sz);
    }
};
```