<!--yml
category: codewars
date: 2022-08-13 11:38:11
-->

# codewars (6 kyu) Which are in?_lhapy的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41746553/article/details/103650237?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-19-103650237-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_41746553/article/details/103650237?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-19-103650237-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 一、题目简介

## 1\. Description:

> Given two arrays of strings a1 and a2 return a sorted array r in lexicographical order of the strings of a1 which are substrings of strings of a2.

> **Example:**
> a1 = [“arp”, “live”, “strong”]
> a2 = [“lively”, “alive”, “harp”, “sharp”, “armstrong”]
> returns [“arp”, “live”, “strong”]

## 2\. 个人理解

**本题就是给定两个字符列表a、b，然后求属于 a，并且为 b 列表中字符串的子串的字符串，将符合要求的字符串组合成数组并排序。
输入：字符串数组 a、b
输出：有序的字符串数组 c**

# 二、代码分析

## 1\. 代码实现

### （1） 失败案例

```
class WhichAreIn
{

  public:
  static std::vector<std::string> inArray(std::vector<std::string> &array1, std::vector<std::string> &array2);
};

std::vector<std::string> WhichAreIn::inArray(std::vector<std::string> &array1, std::vector<std::string> &array2)
{
  std::vector<std::string> ans;
  int len1, len2;
  len1 = array1.size(); len2 = array2.size();
  std::string detectedStr;

  for(int i=0; i<len1; i++)
  {
    detectedStr = array1[i];
    for(int j=0; j<len2; j++)
    {
      if(array2[j].find(detectedStr) != std::string::npos)
        {
          ans.push_back(detectedStr);
          break;
        }
    }
  }

  std::string temp;
  int min_index;
  for(int i=0; i<ans.size()-1; i++)
  {
    min_index = i;
    for(int j=i+1; j<ans.size(); j++)
    {
      if(ans[j] < ans[min_index])  
      {
        min_index = j;
      }
    }
    if(min_index != i)
    {
      temp = ans[i];
      ans[i] = ans[min_index];
      ans[min_index] = temp;
    }
  }

  return ans;
} 
```

> 失败原因：Execution Timed Out (12000 ms)

### （2）成功案例

```
class WhichAreIn
{

  public:
  static std::vector<std::string> inArray(std::vector<std::string> &array1, std::vector<std::string> &array2);
};

std::vector<std::string> WhichAreIn::inArray(std::vector<std::string> &array1, std::vector<std::string> &array2)
{
  std::vector<std::string> ans;
  int len1, len2;
  len1 = array1.size(); len2 = array2.size();
  std::string detectedStr;

  for(int i=0; i<len1; i++)
  {
    detectedStr = array1[i];
    for(int j=0; j<len2; j++)
    {
      if(array2[j].find(detectedStr) != std::string::npos)
      {
        if(ans.size() == 0)
        {  
          ans.push_back(detectedStr);
           break;
        }
        else
        {
          for(std::vector<std::string>::iterator it=ans.begin(); it!=ans.end();it++)
          {
            if(*it > detectedStr)
            {
              ans.insert(it, detectedStr);
              break;
            }
            if( it+1 == ans.end() )
            {
              ans.push_back(detectedStr);
              break;
            }
          }
          break;
        }
      }
    }
  }

  return ans;
} 
```

## 2\. 实现思路

**（1）设置两个缓存器 ans、detectedStr**
       ans：字符串数组，存放符合题目要求的字符串；
       detectedStr：代表当前分析的字符串。

**（2）判断 a 中字符串是否为 b 的子串**
       双重循环，逐个扫描分析 a 中的字符串。

**（3）寻找 ans 中正确的位置存放字符串**
       从首部开始，找到第一个比它大的位置用来存放它。

**link:** [Best Solutions](https://www.codewars.com/kata/which-are-in/solutions/cpp)

## 3\. 收获

**（1）最开始，我是将判断（双重循环）和排序（冒泡排序）分为两个过程，这导致了超时（效率低）**

**（2）改进后，我将判断（双重循环）和排序（插入排序）合在一起，即当判断该字符串满足要求后就计算存放的位置，这样会形成有序的列表，能减少后面插入字符串时的比较次数，提高了效率。**

* * *