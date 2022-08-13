<!--yml
category: codewars
date: 2022-08-13 11:42:43
-->

# 【codewars-7】打印错误_Salted_Sun的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42338512/article/details/123730023?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-22-123730023-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_42338512/article/details/123730023?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-22-123730023-null-null.142^v40^control,185^v2^control&utm_term=codewars)

In a factory a printer prints labels for boxes. For one kind of boxes the printer has to use colors which, for the sake of simplicity, are named with letters from a to m.

The colors used by the printer are recorded in a control string. For example a “good” control string would be aaabbbbhaijjjm meaning that the printer used three times color a, four times color b, one time color h then one time color a…

Sometimes there are problems: lack of colors, technical malfunction and a “bad” control string is produced e.g. aaaxbbbbyyhwawiwjjjwwm with letters not from a to m.

You have to write a function printer_error which given a string will return the error rate of the printer as a string representing a rational whose numerator is the number of errors and the denominator the length of the control string. Don’t reduce this fraction to a simpler expression.

The string has a length greater or equal to one and contains only letters from ato z.
a-m 代表合法的颜色,其它字母为非法颜色. 统计非法颜色数量.

```
Examples:
s="aaabbbbhaijjjm"
printer_error(s) => "0/14"

s="aaaxbbbbyyhwawiwjjjwwm"
printer_error(s) => "8/22" 
```

**要点**

```
class Printer
{
public:
    static std::string printerError(const std::string &s){

      auto errors = std::count_if(s.begin() , s.end() , [](char ch){return ch<'a'||ch > 'm';});

      return std::to_string(errors)+"/"+ std::to_string(s.length());
    }
}; 
```

**另一种解法**

*   使用正则表达式`std::regex`将a-m的字母替换`std::regex_replace`为空串`""`
*   替换后的字符串的长度即为非法字符的个数.

```
#include <regex>

std::regex reg{"[a-m]"} ;
std::string res = std::regex_replace(str,reg,""); 
```