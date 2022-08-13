<!--yml
category: codewars
date: 2022-08-13 11:40:26
-->

# 今天我在Codewars做的第一道题_StrongerIrene的博客-CSDN博客

> 来源：[https://blog.csdn.net/StrongerIrene/article/details/78370294?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-18-78370294-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/StrongerIrene/article/details/78370294?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-18-78370294-null-null.142^v40^control,185^v2^control&utm_term=codewars)

手机关机大满足组大幸福！
题目是这个样子的

英文看的我难受死了，看中文反而成了享受。。。。。
这第一个题叫做 Sum of numbers from 0 to N

```
 #include <string>
#include <iostream>
using namespace std;

class SequenceSum{
  int count;
  public:
  SequenceSum (int);  
  string showSequence();

};

string SequenceSum::showSequence(){

std::string seq = "";
    int tally =0;

    if(count > 0)
    {

         for(int i = 0; i <= count; i++)
         {
         seq += to_string(i); 

         if(i <count)
         seq += "+";

         tally += i;
         }
    }

    else if (count == 0)
    return "0=0";

    else
    return to_string(count) + "<0";

    return seq + " = " + to_string(tally);
}

SequenceSum::SequenceSum (int c) {
  count = c;
}
```

【学到的tostring …
【/**/】
结果跑过去，负数和零可以满足，基础数据和其他数据过不了，这就有点小尴尬了
最后是下面这个版本过了的（核心代码）
* * 可以把构造函数写成（最后面） 类名：类名（int c）：count(c) {}

```
 string myString = "";
    if (count < 0) { myString = to_string(count) + "<0"; return myString; }
    else if (count == 0) {myString = "0=0"; return myString; }
    for (int i = 0; i < count; ++i) {
      myString += to_string(i) + "+";
    }
    myString += to_string(count    ) + " = ";

    myString += count & 1 ? to_string ((count+1) * (count/2) + (1+(count-1)/2)) : to_string((count+1) * (count/2));

    return myString;
    (简洁过头了！） 
```

好的我现在codewars又登不上去了。。。明天把C++里面那些类和 数据结构第二题也写一下吧，代码很重要qwqqqq