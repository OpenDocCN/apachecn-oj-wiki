<!--yml
category: codewars
date: 2022-08-13 11:36:37
-->

# Help the bookseller !（C++CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105906178?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-8-105906178-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/coolsunxu/article/details/105906178?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-8-105906178-null-null.142^v40^control,185^v2^control&utm_term=codewars)

解题思路：

（1）使用map

```
using std::vector;
using std::string;
using std::cout;
using std::endl;
using std::unordered_map;
using std::stringstream;
using std::to_string;

class StockList  {
public:
  static string stockSummary(vector<string> &lstOfArt, vector<string> &categories) {
    if(lstOfArt.size()==0 || categories.size()==0) return "";
    unordered_map<char,int> mp;
    string strc,strn;
    for(auto&& w:lstOfArt) {
      stringstream s(w);
      s>>strc;s>>strn;
      mp[strc[0]]+=atoi(strn.c_str());
    }
    strc = "";
    for(auto&& w:categories) {
      strc = strc+"("+w+" : "+to_string(mp[w[0]])+") - ";
    }
    return strc.substr(0,strc.length()-3);
  }
};
```