<!--yml
category: codewars
date: 2022-08-13 11:47:57
-->

# codewars之C#0001_那个妹子留步的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41995872/article/details/83313308?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-83313308.nonecase](https://blog.csdn.net/weixin_41995872/article/details/83313308?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-83313308.nonecase)

判断一个整数是否是素数，有运行时间要求

```
using System;
public static class Kata
{
  public static bool IsPrime(int n)
  {
    // TODO
       if (n==2||n==3)
        {
            return true;
        }
        if (n%2==0||n<=1)
        {
            return false;
        }
        else
        {
            for (int i = 3; i <= Math.Sqrt(n); i=i+2)
            {
                if (n%i==0)
                {
                    return false;
                }
            }   
            return true;
        }
  }
```

![](img/4c6235c290eb57d96a5e9cd7486149ba.png)