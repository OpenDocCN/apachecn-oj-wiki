<!--yml
category: codewars
date: 2022-08-13 11:50:19
-->

# 【CodeWars】Highest and Lowest_aizhiyan2320的博客-CSDN博客

> 来源：[https://blog.csdn.net/aizhiyan2320/article/details/102114346?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-102114346.nonecase](https://blog.csdn.net/aizhiyan2320/article/details/102114346?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-102114346.nonecase)

##### **Highest and Lowest**

##### **Description:**

In this little assignment you are given a string of space separated numbers, and have to return the highest and lowest number.

**Example:**

```
highAndLow("1 2 3 4 5");  // return "5 1"
highAndLow("1 2 -3 4 5"); // return "5 -3"
highAndLow("1 9 3 4 -5"); // return "9 -5"
```

**Notes:**

*   All numbers are valid Int32, no *need* to validate them.
*   There will always be at least one number in the input string.
*   Output string must be two numbers separated by a single space, and highest number is first.

题意还是很简洁明了，给一串用空格分隔的数字组成的字符串，要求以字符串的形式输出最大的和最小的数字并用空格分隔。

哎，这么简单的题做了好久，还掉了不少坑，自己还是太菜了！！

我的代码：

```
 1 #include<iostream>
 2 #include <algorithm>
 3 #include <sstream>
 4 #include <vector>
 5 using namespace std; 6 
 7 vector<int> v; 8 
 9 int s2i(string s){ //字符串转数字 
10 stringstream ss; 11     int i; 12     ss<<s; 13     ss>>i; 14     return i; 15 } 16 string i2s(int i){ //数字转字符串 
17 stringstream ss; 18     string s; 19     ss<<i; 20     ss>>s; 21     return s; 22 } 23 
24 string highAndLow(const string& numbers){ 25 v.clear(); 26     int p = 0; 27     string a[1005] = {""}; 28     if(numbers.length()==1) return numbers+" "+numbers; 29       for(int i = 0;i<numbers.length();i++){ 30           while(numbers[i]!=' '){ 31                   a[p]+=numbers[i++]; 32 } 33 v.push_back(s2i(a[p])) ; 34         p++; 35 } 36 sort(v.begin(),v.end()); 37       return i2s(v.back())+" "+i2s(v.front()); 38 }
```

我的思路是把所有用字符分隔开的子串保存到新的字符数组里，转成数字，再保存到vector里，对vector所有元素进行排序后，再把最小的数字和最大的数字分别转成字符串输出。

一开始看到题目觉得要分割字符串，先想到的是java里的split函数，可惜c++里没有，就想到了用while循环把不是空格的连续字符一个个储存到字符串数组里。第一次用了append函数，发现append的参数只能是字符串不能是字符，就直接用“+”来连接了。

输出字符串那边还把java和c++弄混了，妄想直接输出v.back()+" "+v.front()....哎！所以无奈下又写了个数字转字符串的函数来输出。

这下觉得万无一失了，测试样样例也对了，高高兴兴的提交，嗯？只有第一个test通过了，后面一律报红。好吧，原来这是一次运行完所有test，每次运行完一个test要手动清空vector的。又加了vector的clear进去，再提交，又报错了，这次是“Exit Code：139”。百度了一下，好像是数组越界之类的问题，发现自己一开始string数组只设置了25个元素，改！改成1005个。这下终于过了。

提交之后发现别人的代码都很简洁，再一次感叹！自己太！菜！了！

话说因为最近要蓝桥杯了，所以一直在用dev-c++，没有自动提示，才发现很多函数啊头文件啊自己根本记不住，每次还都要查，哎。

下面放别人的代码：

```
 1 #include <string>
 2 #include <sstream>
 3 #include <limits>
 4 
 5 std::string highAndLow(const std::string& numbers){ 6   std::stringstream ss(numbers);
 7   int temp, min = std::numeric_limits<int>::max(), max = std::numeric_limits<int>::min();
 8   while (ss >> temp) { 9     min = (temp < min) ? temp : min; 10     max = (temp > max) ? temp : max; 11 }; 12   return std::to_string(max) + " " + std::to_string(min); 13 }
```

大佬就是大佬啊，怎么能把c++的库用的这么6呢？还有就是自己的基本功真的不扎实，stringstream学了不会用。numeric_limits也是涨知识了（相当于INT32_MAX，INT32_MIN），这边还用了c++11新标准的to_string()函数，感觉很好用啊，可惜蓝桥杯要用的5.4.0版本不支持c++11，扎心，java组用的eclipse还有智能提示呢，dev-c++啥也没有。。

```
 1 #include <string>
 2 #include <sstream>
 3 #include <climits>
 4 
 5 std::string highAndLow(const std::string& numbers){ 6     std::stringstream stream(numbers);
 7 
 8     int a = INT32_MAX, b =INT32_MIN;
 9     while(!stream.eof()) { 10         int number; 11         stream>>number; 12         if (number>b) b=number; 13         if (number<a) a=number; 14 } 15 std::stringstream res; 16     res << b << " "<<a; 17     return res.str(); 18 }
```

这是另一个大佬的，思路和上面一个一样。

以后就知道啦，用空格分隔的字符串可以用stringstream直接来做~~

【更新】再补一个大佬的，这个很厉害也很易懂，用set的不可重复和自动排序来做：

```
 1 #include <string>
 2 #include <sstream>
 3 #include <set>
 4 
 5 using namespace std; 6 
 7 string  highAndLow(const string& numbers) { 8   stringstream ss(numbers);
 9   set<int> inumbers; 10   int num; 11   while (ss >> num) { 12 inumbers.insert(num); 13 } 14   return  to_string(*--inumbers.end())  + " " + to_string(*inumbers.begin()); 15 
16 }
```