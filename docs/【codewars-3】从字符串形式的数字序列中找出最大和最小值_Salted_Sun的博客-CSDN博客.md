<!--yml
category: codewars
date: 2022-08-13 11:38:09
-->

# 【codewars-3】从字符串形式的数字序列中找出最大和最小值_Salted_Sun的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42338512/article/details/123709549?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-18-123709549-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_42338512/article/details/123709549?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-18-123709549-null-null.142^v40^control,185^v2^control&utm_term=codewars)

In this little assignment you are given a string of space separated numbers, and have to return the highest and lowest number.

**Examples**

```
highAndLow("1 2 3 4 5");    
highAndLow("1 2 -3 4 5");   
highAndLow("1 9 3 4 -5"); 
```

**Notes**

*   All numbers are valid Int32, no need to validate them.
*   There will always be at least one number in the input string. 输入串中至少含有一个数字。
*   Output string must be two numbers separated by a single space, and highest number is first.

**要点**

*   `sstringstream`实现对字符串用空白进行分割, 并转换为数字. `<sstream>`
*   `numeric_limits` 获取int的上界和下界 作为max/min变量的初始值. `<limits>`
*   `std::to_string` 将数字转换为字符串. `<string>`

**分析**
需要解决的问题主要有两个：用空格分隔出子串；以及将每个子字符串转为数字。
`sstringstream`就能完美解决这个问题。
`sstringstream`默认以空格为分隔符输出字符串，并且通过`ss >> 数字类型变量`完成类型转换.

此外还有一个细节问题, 即`max`和`min`变量的初始值. 因为后续过程中对这两个变量的更新是基于新的数值和`max/min`的比较的.
因此必须选取合适的初值才能使后续的更新正常进行.
对于`max`, 需要选个尽量小的数, 这样数字序列中的最大值才能比它大,进而用该值更新它.对`min`也是类似, 需要选一个尽量大的值作为初始值.

因此需要表示int的上下界.(因为此题目数字范围用int即可描述)
这需要用`numeric_limits`这个类: `std::numeric_limits::max() / min()`

```
#include <string>
#include <sstream>
#include <limits>

std::string highAndLow(const std::string& numbers){

  std::stringstream ss {numbers};

  int max{std::numeric_limits<int>::min()} ;
  int min{std::numeric_limits<int>::max()} ;

  int current{};
  while( ss >> current){
    max = current> max? current : max ;
    min = current< min ? current :min;
  }
  return std::to_string(max)+" " + std::to_string(min);
} 
```