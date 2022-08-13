<!--yml
category: codewars
date: 2022-08-13 11:41:52
-->

# codewars练习(1)_u010082526的博客-CSDN博客

> 来源：[https://blog.csdn.net/u010082526/article/details/84817692?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-26-84817692-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/u010082526/article/details/84817692?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-26-84817692-null-null.142^v40^control,185^v2^control&utm_term=codewars)

Your goal in this kata is to implement a difference function, which subtracts one list from another and returns the result.

本kata的目标是实现一个差异函数，该函数从一个列表减去另一个列表并返回结果。

It should remove all values from list `a`, which are present in list `b`.

它应该从列表a中删除列表b中列出的所有值。

array_diff([1,2],[1]) == [2]

If a value is present in `b`, all of its occurrences must be removed from the other:

如果b列表中只有一个值，那a列表中出现这个值的元素都要删除

array_diff([1,2,2,2,3],[2]) == [1,3]

FUNDAMENTALS基本原理

ARRAYS数组

DATA TYPES数据类型

train

def array_diff(a, b):
    #your code here
    c=[]
    for index,val in enumerate(a):
        if val in b:
            continue
        c.append(val)
    return c

1.Tips: Kata Trainer

Welcome to the kata trainer! A few tips to get you started:

欢迎来到卡塔教练机！让你开始的几个小窍门：

### Attempt

尝试

This button will submit your code against the full set of tests needed to complete the kata.

这个按钮将在完成KATA所需的全部测试中提交您的代码。

### Run Sample Tests

运行样本测试

This button will submit the tests shown within the samples test cases section. Most kata will have provided you some sample tests to get you going, while others will not, in which case some test documentation will be shown instead.

这个按钮将提交在样本测试用例段中显示的测试。大多数kata都会提供一些样例测试来让您继续工作，而另一些则不会，在这种情况下，将显示一些测试文档。

If you care about using TDD, then the sample tests section will be very useful for you. You are encouraged to write your own tests as you try to complete the kata, as you would if you were writing production code.

如果您关心使用TDD，那么示例测试部分将对您非常有用。鼓励您在尝试完成kata时编写自己的测试，就像编写生产代码时一样。

### Production Quality Code

生产质量代码

Some Codewarriors like to write code golfed or creative/clever solutions, but most try to write production quality code. After you have completed all of the test cases (via the attempt button), you will be given an opportunity to cleanup your code so that its "code review" ready.

Some Codewarriors like to write code golfed or creative/clever solutions, but most try to write production quality code. After you have completed all of the test cases (via the attempt button), you will be given an opportunity to cleanup your code so that its "code review" ready.

一些代码勇士喜欢编写高尔夫代码或创造性/聪明的解决方案，但大多数人尝试编写生产质量代码。在您完成了所有的测试用例之后（通过尝试按钮），您将有机会清理您的代码，以便其“代码审查”就绪。

Tips: Solution Voting
You can vote on other Codewarrior's solutions to help uncover the best ones. There are 2 choices for voting:

解决方案投票
你可以投票给其他科德沃的解决方案，以帮助发现最好的。投票有2种选择：

Best Practices

Best practices are for solutions that you think are a good combination of being maintainable and efficient. They may not be the fastest solution - if the fastest solution involves overly optimizing the code in a way that becomes hard to read.

最佳实践

最佳实践是用于您认为可维护性和高效率的良好组合的解决方案。它们可能不是最快的解决方案——如果最快的解决方案涉及以难以阅读的方式过度优化代码。

Clever

Clever votes are for solutions that you feel like are notable in some way, but not something you would expect to see in production code.

聪明的

聪明的投票是针对您认为在某些方面值得注意的解决方案的，但是并不是您期望在生产代码中看到的。