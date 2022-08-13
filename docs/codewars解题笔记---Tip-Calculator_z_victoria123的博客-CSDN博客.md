<!--yml
category: codewars
date: 2022-08-13 11:37:38
-->

# codewars解题笔记---Tip Calculator_z_victoria123的博客-CSDN博客

> 来源：[https://blog.csdn.net/z_victoria123/article/details/86541272?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-86541272.142^v40^control,185^v2^control](https://blog.csdn.net/z_victoria123/article/details/86541272?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-86541272.142^v40^control,185^v2^control)

题目

Complete the function, which calculates how much you need to tip based on the total amount of the bill and the service.

You need to consider the following ratings:

*   Terrible: tip 0%
*   Poor: tip 5%
*   Good: tip 10%
*   Great: tip 15%
*   Excellent: tip 20%

The rating is **case insensitive** (so "great" = "GREAT"). If an unrecognised rating is received, then you need to return:

*   `"Rating not recognised"` in Javascript, Python and Ruby...
*   ...or `null` in Java
*   ...or `-1` in C#

Because you're a nice person, you **always round up** the tip, regardless of the service.

解析

完成函数，它根据账单和服务的总金额计算出你需要付多少小费。

您需要考虑以下评级：

糟糕：小费0%

穷人：小费5%

好：小费10%

伟大：小费15%

优秀：小费20%

评级不区分大小写（所以“great”=“GREAT”）。如果收到未确认的评级，则需要返回：

javascript、python和ruby中的“未识别评级”…

…或null   在Java中在C中…或- 1

因为你是一个好人，不管服务如何，你总是把小费凑齐。

功能解析

传入账单金额和评级，根据不同的评级按照金额和对应应付的小费向上取整，返回小费金额。本题主要考察大小写切换、浮点类型向上取整

我的答案

```
 public static Integer calculateTip(double amount, String rating) {
      double a=0;
        switch (rating.toLowerCase()){
            case "terrible":
                a = 0;
                break;
            case "poor":
                a = amount*0.05;
                break;
            case "good":
                a = amount*0.1;
                break;
            case "great":
                a = amount*0.15;
                break;
            case "excellent":
                a = amount*0.2;
                break;
            default :
                return null;
        }
        double b = Math.ceil(a);//向上取整
        return (int)b;
  }
```

最优的解决方案

```
public static Integer calculateTip(double amount, String rating) {

    switch(rating.toLowerCase()) {
      case "terrible": return 0;
      case "poor": return (int) Math.ceil(amount * 0.05);
      case "good": return (int) Math.ceil(amount * 0.1);
      case "great": return (int) Math.ceil(amount * 0.15);
      case "excellent": return (int) Math.ceil(amount * 0.2);
      default: return null;      
    }   
  }
```