<!--yml
category: codewars
date: 2022-08-13 11:28:51
-->

# python高级练习题:约翰和安报名参加Codewars【难度：3级】--景越Python编程实例训练营,不同难度Python习题，适合自学Python的新手进阶_景越的博客-CSDN博客

> 来源：[https://blog.csdn.net/aumtopsale/article/details/102831156?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-102831156.142^v40^control,185^v2^control](https://blog.csdn.net/aumtopsale/article/details/102831156?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-102831156.142^v40^control,185^v2^control)

## python高级练习题:约翰和安报名参加Codewars【难度:3级】:

约翰和他的妻子安已经决定去Codewars.

在第一天安会做一个习题和约翰 - 他想知道它是如何工作 - 0习题.

让我们叫`A(N)`通过安在一天`N`做练习题的数量.我们有一个`(0)= 1`和以相同的方式`Ĵ(0)= 0`(或’一(1)= 1`和`Ĵ(1)= 0`对于具有具有索引开始数组矩阵语言在1).

他们选择了以下规则:

*   在天`N`通过安做练习题的数量应该是`N`减去约翰在一天`t`做练习题的数量,`t`等于做练习题数量
    通过安在她`n天 - 1`.

*   在天`N`约翰做练习题的数量应该是`N`减去安在天`t`做练习题的数量,`t`等于做练习题数量
    约翰自己在`n天 - 1`.

哎呦!我认为他们需要制定出更清晰一点正是那里竟然要自己进去!

# 你能写:

*   1)两种功能`ann`和’约翰(参数n)`给练习题安和约翰的号码列表应在第一n天(见下面的首批实例)?
*   2)采取安`函数sum_ann(n)的`和John`函数sum_john(n)的`练习题总数 - 在所述第一n天?

在1的功能)在Fortran中没有测试和壳牌未经测试.

# 例子:

```
 约翰(11) - > [0,0,1,2,2,3,4,4,5,6,6]
安(6) - > [1,1,2,2,3,3]

sum_john(75) - > 1720
sum_ann(150) - > 6930 
```

# 壳牌注意:

sumJohnAndAnn有两个参数:

第一种:N(天数,$ 1)

第二一项:($ 2) - >

请参阅"抽样检验".

# 注意:

保持性能的眼睛.

## 编程目标:

```
def john(n):

def ann(n):

def sum_john(n):

def sum_ann(n): 
```

## 测试样例:

```
def testJohn(n, res):
    Test.assert_equals(john(n), res)
def testAnn(n, res):
    Test.assert_equals(ann(n), res)
def testSumJohn(n, res):
    Test.assert_equals(sum_john(n), res)
Test.describe("john")
Test.it("Basic tests")
testJohn(11, [0, 0, 1, 2, 2, 3, 4, 4, 5, 6, 6])
Test.describe("ann")
Test.it("Basic tests") 
```

## 最佳答案(多种解法):

[点击查看答案](http://dd.ma/sUlIkTYs)

## 更多关联题目:

[python基础练习题:最接近零【难度:1级】–景越Python编程实例训练营,不同难度Python习题,适合自学Python的新手进阶](https://blog.csdn.net/aumtopsale/article/details/102792093)

## 交流讨论:

[![Python基础训练营](img/9ddc589a9bae9dd81334056da3504a2c.png "Python基础训练营")景越Python基础训练营QQ群](//shang.qq.com/wpa/qunwpa?idkey=c10499c0a2daa9cc444ea9695745b4919a58202d6abdc107e1ed42882d604d5b)
![在这里插入图片描述](img/7212073a4e753731a08f404f4ada9768.png)
欢迎各位同学加群讨论,一起学习,共同成长!

## 免责申明:

本博客所有编程题目及答案均收集自互联网,主要用于供网友学习参考,如有侵犯你的权益请联系管理员及时删除,谢谢
<font size="1">题目收集至https://www.codewars.com/</font>
<font size="1">https://www.codewars.com/kata/john-and-ann-sign-up-for-codewars</font>