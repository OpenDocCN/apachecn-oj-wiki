<!--yml
category: codewars
date: 2022-08-13 11:35:54
-->

# Multiplying numbers as strings（C++CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/115760490?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058616781685360739%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058616781685360739&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-18-115760490-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/coolsunxu/article/details/115760490?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058616781685360739%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058616781685360739&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-18-115760490-null-null.142^v40^control,185^v2^control&utm_term=codewars)

```
#include <iostream>
#include <string>

using namespace std;

string multiply(string a, string b) {
  vector<int> v(a.length()+b.length(),0);
  for(int i=0;i<a.length();i++) {
    for(int j=0;j<b.length();j++) {
      v[i+j+1]+=(a[i]-'0')*(b[j]-'0');
    }
  }

  for(int i=a.length()+b.length()-1;i>0;i--) {
    v[i-1]+=v[i]/10;
    v[i]%=10;
  }

  int i=0;
  while(i<v.size() && v[i]==0) i++;

  string str="";
  while(i<v.size()) str+=to_string(v[i++]);
  if(str=="") return "0";
  else return str;
}
```