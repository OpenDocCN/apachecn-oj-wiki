<!--yml
category: codewars
date: 2022-08-13 11:33:08
-->

# 在Codewars中的c++练习_linlin:D的博客-CSDN博客

> 来源：[https://blog.csdn.net/saroyamal/article/details/119133459?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036053316781667833427%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036053316781667833427&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-23-119133459-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/saroyamal/article/details/119133459?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036053316781667833427%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036053316781667833427&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-23-119133459-null-null.142^v40^control,185^v2^control&utm_term=codewars)

工作原因需要学习c++

为了速成直接从简单的codewars练起

记一下。

# 8 kyu题库

这个是最简单的级别

## Fake Binary

这一题居然卡了我好久。。。怪我，怪我不知道ASCII码。
。。。

```
#include <string>

std::string fakeBin(std::string str){
  std::string result;
  int N=str.size();
  for (int i=0;i<N;i++){
    int n = str[i]-'0'; \\这一步真的贼重要，一定要写那个'0', 如果不写的话，你的n就是ASCII码里对应的那个值。比如说1是49.
    if (n<5) result+='0';else result+='1';
    }
  return result;
} 
```

果然我还是太菜了，真的卡得我欲仙欲死啊。。。用typeid.name() (记得include )一点点查变量类型。。。查到一个是char的……

```
#include <string>

std::string fakeBin(std::string str){
  for (int i=0;i<str.size();i++){
    str[i]=((str[i]-'0')<5?'0':'1');
  }
  return str;
} 
```

## Convert boolean values to strings ‘Yes’ or ‘No’.

```
using namespace std;

string bool_to_word(bool value)
{
  if (value) {
  return "Yes";
}
 else {
   return "No";
 }

} 
```

或者直接用

```
return value ? "Yes" : "No"; 
```

## Square(n) Sum

考察vector用法：求vector内值平方和

```
#include <vector>

int square_sum(const std::vector<int>& numbers)
{
    int N = 0;
    int s = numbers.size();
  for (int i=0;i<s;i++){
  N += numbers[i]*numbers[i];
  }
  return N;
} 
```

```
#include <vector>
int square_sum(const std::vector<int>& numbers)
{
    int ret=0;
    for (auto x:numbers) ret+=(x*x);
    return ret;
} 
```

这个auto x :numbers是啥操作？

# 7 kyu题库

## Vowel Count

很简单，随便做都能做出来，但是别人结构很好。这边用的是lambda表达式匿名函数。新知识点get。可以看[这篇文章](https://blog.csdn.net/a379039233/article/details/83714770?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162752711616780269828055%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=162752711616780269828055&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~baidu_landing_v2~default-1-83714770.pc_v2_rank_blog_default&utm_term=lamda%E8%A1%A8%E8%BE%BE%E5%BC%8F+c%2B%2B&spm=1018.2226.3001.4450)

```
#include <string>

using namespace std;

int getCount(const string& inputStr){
  return count_if(inputStr.begin(), inputStr.end(), [](const char ch) {
      switch(ch) {
          case 'a':
          case'e':
          case'i':
          case'o':
          case'u':
              return true;
          default:
              return false;} 
     });
} 
```

## Exes and Ohs

每一次都会有一点意料之外的问题

```
#include <iostream>
#include <algorithm>
#include <string>
using namespace std;
bool XO(const string& str)
{
  string temp;
  temp.assign(str);
  transform(temp.begin(), temp.end(), temp.begin(), ::tolower);
    int xnum = count(temp.begin(),temp.end(),'x');
    int onum = count(temp.begin(),temp.end(),'o');
  return xnum == onum;
} 
```

## Fixing String Case

如果字符串中大写字母多，就把他变成全大写。反之全小写。c++转换大小写居然这么烦。。。
注意一下通过ascii判断大小写和transform函数。

```
#include<iostream>
#include<string>
#include<algorithm>
using namespace std;

string solve(string s){
  int i,l(0),b(0);
  i=s.length();
  for(int j=0;j<i;j++)
{
if('a'<=s[j]&&s[j]<='z')
l++;
if('A'<=s[j]&&s[j]<='Z')
b++;
}
  if (b>l) transform(s.begin(), s.end(), s.begin(), ::toupper);
else transform(s.begin(), s.end(), s.begin(), ::tolower);
  return s;
} 
```

## Highest and Lowest

给你{1 2 3 4 5}, 返回{max, min}

```
#include <string>
#include <sstream>
#include <cstring>
using namespace std;

string highAndLow(const string& numbers){
  istringstream is(numbers);
  string s;
  is >> s;
  int max = stoi(s);
  int min = stoi(s);
  while (is >> s){
    if (max < stoi(s))max = stoi(s);
    if (min > stoi(s))min = stoi(s);
  }
  string result;
  result = to_string(max) + " " + to_string(min);
  return result;

} 
```

## Testing 1-2-3

主要问题在于如何将一个整数加入字符串。使用std::to_string(数字)就好。

```
#include <string>
#include <vector>

std::vector<std::string> number(const std::vector<std::string> &lines)
{
  std::vector<std::string> result;  
  std::string str;
  for (int i=0;i<lines.size();i++) {
    int n = i + 1;
    str = std::to_string(n) + ": " + lines[i];
    result.push_back(str);
  }
  return result;
} 
```

可以用流，但我还不太会。

## Reverse words

这一题做不出来啊，有点难啊……最多做成这样……

```
#include <iostream>
#include <sstream>
#include <string>
#include <algorithm>
#include <regex>
using namespace std;

int main()
{   string str = "double  spaced  words";

	istringstream is(str);  
    string s, r, m;  
    while(is >> s){
	int n = s.size();
        m.assign(s);
        for (int i=0;i<n;i++){
        m[i] = s[n-1-i];
        }
        r += m + " ";
        }
    r.pop_back();

     return 0;
} 
```

看别人的真的很好啊

```
std::string reverse_words(std::string str)
{
  std::string out;
  std::string cword;
  for (char c : str) {
    if (c == ' ') {
      out += cword;
      out += c;
      cword = "";
      continue;
    }
    cword = c + cword;
  }
  out += cword;
  return out;
} 
```

可能这就是逻辑吧。。。

## Complementary DNA

字符串中AT互换，CG互换

```
#include <string>
#include<iostream> 
using namespace std;

int main(){

string dna = "CATG";
string rna;
int N = dna.size();
for (int i = 0; i < N; i++){
switch(dna[i]){
	case 'A': rna.push_back('T'); break;
	case 'T': rna.push_back('A'); break;
	case 'C': rna.push_back('G'); break;
	case 'G': rna.push_back('C'); break;
}
}
cout << dna << endl;
cout << rna << endl;
cout << dna.size() << endl;

return 0 ;

} 
```

或者把const改掉可以写的更简洁一点。

```
std::string DNAStrand(std::string dna)
{
  for(int i=0;i<dna.length();i++) {
    switch (dna[i]) {
    case 'A': dna[i]='T'; break;
    case 'T': dna[i]='A'; break;
    case 'C': dna[i]='G'; break;
    case 'G': dna[i]='C'; break;
    }
  }
  return dna;
} 
```

或者用map

```
#include <map>

const std::map<char, char> mapping =
{
  {'A', 'T'},
  {'T', 'A'},
  {'C', 'G'},
  {'G', 'C'},
};

std::string DNAStrand(std::string dna)
{
  for (char& c : dna)
  {
    c = mapping.at(c);
  }
  return dna;
} 
```

## Sum of the first nth term of Series

求数列和并保留两位小数转为字符串

```
#include <iostream>
#include <string>
#include <sstream>
#include <iomanip>
using namespace std;
string seriesSum(int n)
{
double s = 0.00;
	for (double i=1;i<=n;i++) s += 1/(3*i-2);
	ostringstream ss;
	ss <<std::setiosflags(std::ios::fixed) << std::setprecision(2) << s;
	string result(ss.str());
  return result;
} 
```

累了，一会儿再看别人的。

# 6 kyu题库

## IPv4 to int32

这一题好难啊。。。。
我一开始以为很简单。。。
没想到它专挑我不会的地方打。。。
题干就是给你一个ipv4地址比如说xxx.xx.xx.x，让你把它变成一个32位的二进制数，再转化成10进制。

```
#include <cstdint>
#include <string>

uint32_t ip_to_int32(const std::string& ip) 
{
    uint32_t a, b, c, d;
    a = b = c = d = 0;
    sscanf(ip.c_str(), "%u.%u.%u.%u", &a, &b, &c, &d);
    return d | (c << 8) | (b << 16) | (a << 24);
} 
```

人家是这么解决的；
我是这么解决的
我多少有点智障。。。。

```
#include <cstdint>
#include <string>
#include <cstring>
#include <sstream>
#include <bitset>
#include <vector>
using namespace std;

uint32_t ip_to_int32(const std::string& ip) {
      vector<string> num;
  string temp;
  stringstream ss(ip);
  int i = 0;
  while (getline(ss,temp,'.'))num.push_back(temp);

  bitset<8>a1(stoi(num[0]));
  bitset<8>a2(stoi(num[1]));
  bitset<8>a3(stoi(num[2]));
  bitset<8>a4(stoi(num[3]));
  string m1=a1.to_string();
  string m2=a2.to_string();
  string m3=a3.to_string();
  string m4=a4.to_string();
  string a = m1+m2+m3+m4;

  bitset<32> bs(a);
  string result = to_string(bs.to_ulong());

  istringstream is(result);
  unsigned int ui = -1;

  is>>ui;

  return ui;

} 
```

## Unwanted Dollars

这一题做了比较久，主要是理解不到位。

```
#include <string>
#include <algorithm>
#include <cstdlib>
using namespace std;

double money_value(const string &s)
{
  string str = s;

  string::size_type idx2 = str.find("$");
  if (idx2 != string::npos){
        auto itor2 = remove(str.begin(),str.end(),'$');
    str.erase(itor2, str.end());
  };

  string::size_type idx = str.find(" ");
  if (idx != string::npos) {
    auto itor = remove(str.begin(),str.end(),' ');
    str.erase(itor, str.end());
  }

try
  {stod(str);}catch(...){return 0.0;}return stod(str);} 
```

别人的解法参考

```
using namespace std;
#include <string>

double money_value(const string &s)
{
string buffer(s);
buffer.erase(std::remove(buffer.begin(), buffer.end(), '$'), buffer.end()); 
buffer.erase(std::remove(buffer.begin(), buffer.end(), ' '), buffer.end()); 

return atof(buffer.c_str()); 
} 
```

## Design a Simple Automaton(Finite State Machine)

这个感觉蛮实用的，做一下。

```
class Automaton
{
public:
  Automaton();
  bool read_commands(const std::vector<char>& commands);

};

Automaton::Automaton(){}

 bool Automaton::read_commands(const std::vector<char>& commands){
    int state = 1;
    int N = commands.size();
    for (int i=0;i<N;i++){
      int e = commands[i]-'0';
      switch (state){
        case 1: if (e==1) state=2; else state=1; break;
        case 2: if (e==1) state=2; else state=3; break;
        case 3: state=2; break;
      }
    }
    if (state==2) return true;else return false;
  }; 
```

# 5 kyu题库

## A Chain adding function

这一题感觉很难，而且主要是没有什么思路。以后记得回来看看。
虽然还是不会做，但找了答案，分析一下。主要涉及运算符()的重载

```
class add
{
public:
	//初始化参数列表
    add (int x) : _x( x ) { }
    //重载int()操作符
    operator int() { return _x; }
    //重载操作符()(int y)为
    add operator() (int y) { return add(_x + y); }
    //
    friend bool operator==(const int& a, const add& b) { return a == b._x; }

private:
    int _x;
}; 
```

其实还是没太看懂，慢慢来吧

## Maximum subarray sum

动态规划问题

```
#include <vector>

using namespace std;

int maxSequence(const vector<int>& arr) {
  int localmax=0;
  int globalmax=0;
  for (int i = 0;i<arr.size();i++)
  {
    localmax = localmax + arr[i];
    if (localmax > globalmax)
      globalmax = localmax;
    if (localmax < 0)
      localmax = 0;
  }
  return globalmax;
} 
```

```
#include <vector>
using namespace std;
//c++自带max
int maxSequence(const vector<int>& arr){
    int res = 0, sum = 0;
    for(int e:arr) res=max(res,sum=max(sum+e,e));
    return res;
} 
```

# 4kyu题库

## Snail

顺时针遍历二维矩阵

```
#include <vector>
using namespace std;

std::vector<int> snail(const std::vector<std::vector<int>> &snail_map) {
  int N = snail_map[0].size();
  int M = snail_map.size();
  vector<int> res={};
  int m0 = 0;
  int n0 = 0;

  while (n0<N && m0<M){
    for (int i=n0;i<N;i++) res.push_back(snail_map[m0][i]);
    for (int i=m0+1;i<M;i++) res.push_back(snail_map[i][N-1]);
    if (m0<(N-1) && n0<(N-1)){
      for (int i=N-2;i>=n0;i--) res.push_back(snail_map[M-1][i]);
      for (int i=M-2;i>m0;i--) res.push_back(snail_map[i][n0]);
    }
    m0++;
    n0++;
    N--;
    M--;
  }
  return res;
} 
```

我写的还是不太清楚，对比人家的。

```
#include <vector>
using namespace std;
inline vector<int> snail(vector<vector<int>> array) {
  int leftlimit=0, uplimit=0, rightlimit=array[0].size()-1, downlimit=rightlimit, cx=-1, cy=-1;
  vector <int> ans;
  while (leftlimit<=rightlimit){
    for (cy++, uplimit++,    cx++; cx <= rightlimit; cx++) ans.push_back(array[cy][cx]); 
    for (cx--, rightlimit--, cy++; cy <= downlimit ; cy++) ans.push_back(array[cy][cx]);
    for (cy--, downlimit--,  cx--; cx >= leftlimit ; cx--) ans.push_back(array[cy][cx]);
    for (cx++, leftlimit++,  cy--; cy >= uplimit   ; cy--) ans.push_back(array[cy][cx]);
  } 
  return ans;
} 
```