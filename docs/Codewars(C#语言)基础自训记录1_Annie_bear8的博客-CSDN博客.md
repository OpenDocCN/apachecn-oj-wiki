<!--yml
category: codewars
date: 2022-08-13 11:26:54
-->

# Codewars(C#语言)基础自训记录1_Annie_bear8的博客-CSDN博客

> 来源：[https://blog.csdn.net/Annie_bear8/article/details/120622555?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-120622555.142^v40^control,185^v2^control](https://blog.csdn.net/Annie_bear8/article/details/120622555?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-120622555.142^v40^control,185^v2^control)

# CodeWars(C#语言)基础自训记录1

## 序言

本人C#语言小白，秉持着学习编程边学边练的要义，接触到了Codewars这个网站 [Codewars](https://www.codewars.com/dashboard)，从最底层的8kyu开始，进一步了解到了C#的各种用法，在这里也是做一个我接触过的题目的汇总，自我复习的同时也供大家参考一下。

之后的自训记录也会像今天这样，内容包括题目，我自己第一次解答给出的Solutions，个人对于题目的解读，其中部分题目也会附带有答案区我认为比较优秀的Solutions。

## 基础自训记录1

**1\. Convert a Number to a String**
***Details:***
We need a function that can transform a number into a string.
What ways of achieving this do you know?
***Examples:***
123 --> “123”
999 --> “999”
***My Solution:***

```
using System;
public class Kata
{
  public static string NumberToString(int num)
  {
    return num.ToString();
  }
} 
```

***Tips:***
考察的知识点为如何将数字转换为字符串，主要的应用的方法为.ToString()

**2\. Return Negative**
***Details:***
In this simple assignment you are given a number and have to make it negative. But maybe the number is already negative?
***Examples:***
Kata.MakeNegative(1); // return -1
Kata.MakeNegative(-5); // return -5
Kata.MakeNegative(0); // return 0
***My Solution:***

```
using System;
public static class Kata
{
  public static int MakeNegative(int number)
  {
    if(number>0)
      {
      number = -number;
    }
    else
      number = number;
    return number;
  }
} 
```

***Other Solution:***

```
using System;
public static class Kata
{
  public static int MakeNegative(int number)
  {
    return -Math.Abs(number);
  }
} 
```

***Tips:***
本题本人第一反应是使用 if 判断语句完成，看了答案区发现用 Math 库也是一种很好的方式。

**3\. Square(n) Sum**
***Details:***
Complete the square sum function so that it squares each number passed into it and then sums the results together.
***Examples:***
For [1, 2, 2] it should return 9 because 1<sup>2</sup> + 2<sup>2</sup> + 2<sup>2</sup> = 9.
***My Solution:***

```
public static class Kata
{
  public static int SquareSum(int[] n)
  { 
    int sum = 0;
    for(int i=0;i<n.Length;i++)
      {
        sum += n[i]*n[i];
      }
    return sum;
  }
} 
```

***Other Solution:***

```
using System.Linq;
public static class Kata
{
  public static int SquareSum(int[] n) => n.Sum(i => i * i);
} 
```

***Tips:***
这里就体现出了库的一些好处了，本人是使用的 for 循环解决的，但如果调用Linq库就能简化代码，这里也是推给大家一篇学习Linq库的文章[【C#】System.Linq，万能的查询语句](https://blog.csdn.net/qq_39108767/article/details/86648448?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522163332910816780366554355%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=163332910816780366554355&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-86648448.pc_search_result_control_group&utm_term=System.Linq&spm=1018.2226.3001.4187)

**4\. Descending Order**
***Details:***
Your task is to make a function that can take any non-negative integer as an argument and return it with its digits in descending order. Essentially, rearrange the digits to create the highest possible number.
***Examples:***
Input: 42145 Output: 54421
Input: 145263 Output: 654321
Input: 123456789 Output: 987654321
***My Solution:***

```
using System;
public static class Kata
{
  public static int DescendingOrder(int num)
  {
    int [] train = new int[20];
    int k = num.ToString().Length;

    for(int i=0;i<k;i++)
      {
      train[i]=num%10;
      num/=10;
    }
    Array.Sort(train);
    Array.Reverse(train);
    int output = 0;
    for(int j=0;j<k;j++){
      output*=10;
      output+=train[j];
    }
    return output;
  }
} 
```

***Other Solution:***

```
using System;
using System.Linq;
public static class Kata
{
  public static int DescendingOrder(int num)
  {
    return int.Parse(string.Concat(num.ToString().OrderByDescending(x => x)));
  }
} 
```

***Tips:***
这道题我做完还是比较有收获的，学会了对于数组的一系列操作，包括巧用 % 取出数字，又如何将数字组合成一个 int 类型的数字输出。

**5\. Mumbling**
***Details:***
This time no story, no theory. The examples below show you how to write function accum.
***Examples:***
accum(“abcd”) -> “A-Bb-Ccc-Dddd”
accum(“RqaEzty”) -> “R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy”
accum(“cwAt”) -> “C-Ww-Aaa-Tttt”
***My Solution:***

```
using System;
public class Accumul 
{
  public static String Accum(string s) 
  {
    string result = "";
    char [] stringArray = s.ToCharArray();
    for(int i=0;i<stringArray.Length;i++)
    {
      char.ToLower(stringArray[i]);
      for(int j=0;j<=i;j++)
      {
        if(j==0)
          result = result + char.ToUpper(stringArray[i]);
        else
          result = result + char.ToLower(stringArray[i]);
      }
      if(i!=stringArray.Length-1)
        result = result +"-";
    }
    return result;
  }
} 
```

***Other Solution:***

```
using System;
using System.Linq;
public class Accumul 
{
  public static String Accum(string s) 
  {
     return string.Join("-",s.Select((x,i)=>char.ToUpper(x)+new string(char.ToLower(x),i)));
  }
} 
```

***Tips:***
本人这道题是卡了挺久的，主要是一开始不会使用.ToCharArray()的方法，后来发现这个方法可以很轻松地将字符串存放到数组中进行操作，包括一些诸如.ToLower()的方法也能很好帮助我们解决问题。

## 小结

因为是刚开始接触Codewars，这也是我的第一篇博客，努力做了一个尝试，上传的题目都很基础，写的过程主要是我自己能复习一遍思路。五道题目前三道难度属于8kyu，后两题是7kyu，难度有个小小的递增趋势。个人认为Codewars是很优秀的自我训练平台，答案区的各种大佬的答案也让我大开眼界，也越发觉得自己的基础薄弱，希望自己之后能在编程的路上越走越远！