<!--yml
category: codewars
date: 2022-08-13 11:39:57
-->

# csharp高级练习题:Codewars风格排名系统【难度：4级】--景越C#经典编程题库,不同难度C#练习题，适合自学C#的新手进阶训练_goodview andyldm的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_45444821/article/details/103301898?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-103301898.142^v40^control,185^v2^control](https://blog.csdn.net/weixin_45444821/article/details/103301898?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-103301898.142^v40^control,185^v2^control)

## csharp高级练习题:Codewars风格排名系统【难度:4级】:

写一类称为用户被用来计算用户将通过一个类似于Codewars用途排名系统进展的量.

##### 商业规则:

*   用户开始于秩-8,可以进步一路8.
*   没有0(零)排名.接下来的排名后-1 1.
*   用户将完成的活动.这些活动也有行列.
*   每次用户完成排名活动的用户等级进度更新基于活动的等级的关
*   从完成的活动赚取的进步是相对于什么用户当前的等级是相对于活动的等级
*   用户的排名进步在零开始了,每个时代的进步达到100用户的级别升级到一个新的水平
*   任何剩余的进步赢得而在此前的排名将朝着下一个等级的进步被应用(不抛出任何进展的距离).唯一的例外是,如果有留下来走向进步没有其他等级(一旦你达到等级8没有更多进展).
*   用户不能超过8级的进展.
*   等级值的唯一可接受的范围为-8,-7,-6,-5,-4,-3,-2,-1,1,2,3,4,5,6,7,8.任何其他值应该提出一个错误.

进度打进像这样:

*   完成该排名相同用户的将是价值300点的活动
*   完成是一个排名比排名用户的下一个活动将是得1分
*   任何活动完成了在排名2级或比用户的排名将被忽略,更多的低
*   完成的活动比目前用户的等级将加快发展等级排名较高.越大的排名之间的差异就越进展将会增加.式是`10 *d* D`其中`D`等于在活动和用户之间的排名的差异.

##### 逻辑实例:

*   如果用户排名-8完成的活动排名-7他们将获得10个进度
*   如果用户排名-8完成的活动排名-6他们将获得40个进度
*   如果用户排名-8完成的活动排名-5他们将获得90个进度
*   如果用户排名-8完成活动排名-4他们将获得160进展,导致用户升级到秩-7和具有获得对他们的下一个秩60个进展
*   如果用户排名-1完成的活动排名第一,他们将获得10个进步(记住,零等级被忽略)

##### 代码使用的例子:

```
VAR =用户新的用户()
user.rank 
user.progress 
user.incProgress(-7)
user.progress 
user.incProgress(-5)
现在user.progress#=> 0 
user.rank#=> -7 
```

```
用户=新用户()
user.rank#=> -8
user.progress#=> 0
user.incProgress(-7)
user.progress#=> 10
user.incProgress(-5)# 将增加90个进度
现在user.progress#=> 0# 进展是零
user.rank#=> -7# 秩升格为-7 
```

```
USER = User.new
user.rank
user.progress
user.inc_progress(-7)
user.progress
user.inc_progress(-5)
现在user.progress
user.rank 
```

```
用户=用户()
user.rank
user.progress
user.inc \ _progress(-7)
user.progress
user.inc \ _progress(-5)
现在user.progress
user.rank 
```

```
用户的用户=新用户();
user.rank; 
user.progress; 
user.incProgress(-7);
user.progress; 
user.incProgress(-5); 
user.progress;现在
user.rank; 
```

```
秩NEWUSER  -  => -8
进展NEWUSER  -  => 0
让U2 = incProgress(-7)NEWUSER
进展U2  -  => 10
让U3 = incProgress(-5)U2  - 将增加90个进度
进展U3  -  => 0  - 现在进步是零
秩U3  -  => -7  - 秩升格为-7 
```

```
用户的用户=新用户();
user.rank; 
user.progress; 
user.incProgress(-7);
user.progress; 
user.incProgress(-5); 
user.progress;现在
user.rank; 
```

```
** 注:** ** 在** Java的一些方法可能会抛出一个`IllegalArgumentException`. 
```

```
** 注:** ** 在C#** 一些方法可能会抛出一个`ArgumentException`. 
```

** 注意**:Codewars不再使用该算法为自己的排名系统.它采用了基于纯数学的解决方案,给出了一致的结果,无论什么样的顺序一组排名活动正在完成.

## 编程目标:

## 测试样例:

```
namespace Solution {
  using NUnit.Framework;
  using System;

  [TestFixture]
  public class SolutionTest
  {
    public void MyTest()
    {
      Assert.AreEqual("expected", "actual");
    }
  }
} 
```

## 最佳答案(多种解法):

[点击查看答案](http://dd.ma/1UvBCknY)

## 更多关联题目:

[csharp基础练习题:TO DE-RY-PO-陆琪暗号【难度:1级】–景越C# 经典编程题库,不同难度C# 练习题,适合自学C# 的新手进阶训练](https://blog.csdn.net/weixin_45444821/article/details/103286670)
[csharp进阶练习题:号码动物园巡逻【难度:2级】–景越C# 经典编程题库,不同难度C# 练习题,适合自学C# 的新手进阶训练](https://blog.csdn.net/weixin_45444821/article/details/103288010)

## 免责申明

本博客所有编程题目及答案均收集自互联网,主要用于供网友学习参考,如有侵犯你的权益请联系管理员及时删除,谢谢
<font size="1">题目收集至https://www.codewars.com/</font>
<font size="1">https://www.codewars.com/kata/codewars-style-ranking-system</font>