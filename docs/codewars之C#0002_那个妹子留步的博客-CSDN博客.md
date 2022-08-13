<!--yml
category: codewars
date: 2022-08-13 11:40:39
-->

# codewars之C#0002_那个妹子留步的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41995872/article/details/83313145?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-25-83313145-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_41995872/article/details/83313145?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-25-83313145-null-null.142^v40^control,185^v2^control&utm_term=codewars)

给定一个数组，将等效二进制值转换为整数。

例如：[0,0,0,1]被视为0001，它是1的二进制表示。

例子：

```
`Testing: [0, 0, 0, 1] ==> 1
Testing: [0, 0, 1, 0] ==> 2
Testing: [0, 1, 0, 1] ==> 5
Testing: [1, 0, 0, 1] ==> 9
Testing: [0, 0, 1, 0] ==> 2
Testing: [0, 1, 1, 0] ==> 6
Testing: [1, 1, 1, 1] ==> 15
Testing: [1, 0, 1, 1] ==> 11` 
```

但是，阵列可以具有不同的长度，而不仅限于`4`。

普通方法：

```
using System;
namespace Solution
{

  class Kata
    {
      public static int binaryArrayToNumber(int[] BinaryArray)
        {
          //Code here
            double number = 0;
        for (int i = 0; i < BinaryArray.Length; i++)
        {
            number+=Math.Pow(2, BinaryArray.Length-1-i)* BinaryArray[i];
        }

        return  (int)number;
        }
    }
}
```

codewars巧妙方法：

```
using System;
namespace Solution
{
  class Kata
    {
      public static int binaryArrayToNumber(int[] BinaryArray)
        {
          //将二进制装换成十进制
          return Convert.ToInt32(string.Join("", BinaryArray), 2);
        }
    }
}
```

![](img/4c6235c290eb57d96a5e9cd7486149ba.png)