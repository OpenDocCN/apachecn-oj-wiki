<!--yml
category: codewars
date: 2022-08-13 11:38:36
-->

# [codewars][python][C++]Mumbling_sjtubn的博客-CSDN博客

> 来源：[https://blog.csdn.net/sjtubn/article/details/87876226?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-87876226.142^v40^control,185^v2^control](https://blog.csdn.net/sjtubn/article/details/87876226?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-87876226.142^v40^control,185^v2^control)

This time no story, no theory. The examples below show you how to write function `accum`:

**Examples:**

```
accum("abcd") -> "A-Bb-Ccc-Dddd"
accum("RqaEzty") -> "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
accum("cwAt") -> "C-Ww-Aaa-Tttt" 
```

The parameter of accum is a string which includes only letters from `a..z` and `A..Z`.

思路：遍历拼接字符串，使用upper和lower函数

代码如下：

【python】

def accum(s):
    count=0
    ret=''
    for i in s:
        count+=1
        ret+=i.upper()
        for index in range(count-1):
            ret+=i.lower()
        if count<len(s):
            ret+='-'
    return ret

"Best One

def accum(s):
    return '-'.join(c.upper() + c.lower() * i for i, c in enumerate(s))

【C++】

class Accumul
{
public:
    static std::string accum(const std::string &s);
};

std::string Accumul::accum(const std::string &s)
{
    int length = s.size();
    int count = 0;
    std::string ret = "";
    for (int i = 0; i < length; i++)
    {
        char upc = s[i];
        char lowc = s[i];
        if (upc > 'Z')
        {
            upc += ('A'-'a');
        }
        else
        {
            lowc -= ('A'-'a');
        }
        count++;
        ret += upc;
        ret += std::string(count - 1, lowc);
        if (count < length)
        {
            ret += "-";
        }
    }
    return ret;
}

"Best One

class Accumul
{
public:
    static std::string accum(const std::string &s) {
      std::string result;
      for (int i = 0; i < s.length(); i++) {
        result.append("-");
        result.append(std::string(1,toupper(s[i])));
        result.append(std::string(i,tolower(s[i])));
      }
      return result.substr(1,result.length());
    }
};