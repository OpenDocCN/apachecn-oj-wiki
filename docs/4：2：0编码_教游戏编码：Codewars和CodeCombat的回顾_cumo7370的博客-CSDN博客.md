<!--yml
category: codewars
date: 2022-08-13 11:27:17
-->

# 4:2:0编码_教游戏编码：Codewars和CodeCombat的回顾_cumo7370的博客-CSDN博客

> 来源：[https://blog.csdn.net/cumo7370/article/details/107396702?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-107396702.142^v40^control,185^v2^control](https://blog.csdn.net/cumo7370/article/details/107396702?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-107396702.142^v40^control,185^v2^control)

4:2:0编码

最近[，](https://www.reddit.com/r/Python/comments/3bgjud/you_sit_down_with_your_machine_and_a_person_who/csmd4yz)我[偶然发现了](https://www.reddit.com/r/Python/comments/3bgjud/you_sit_down_with_your_machine_and_a_person_who/csmd4yz)两个学习编码和编程技能的网站： [CodeCombat](http://codecombat.com/)和[Codewars](http://Codewars.com/) 。 两者都使用免费软件原理（所有代码示例都是开放源代码[许可的](http://www.gnu.org/licenses/license-list.en.html)和/或[GitHub](https://github.com/codecombat) ），并帮助教授不同的计算机编程语言。 当我的一些学生寻求学习[Python](http://python.org/)编程语言时，我测试了CodeCombat和Codewars。

## CodeCombat

<sup>屏幕快照由Horst Jens提供。</sup> <sup>[CC BY-SA 4.0](https://creativecommons.org/licenses/by/4.0/) 。</sup>

CodeCombat专注于游戏化，使其适合年轻观众。 如果您喜欢带有卡通幻想图形的RPG游戏，您也将很喜欢。 该游戏基于[Rurple](https://en.wikipedia.org/wiki/RUR-PLE)和[Karel](https://en.wikipedia.org/wiki/Karel_%28programming_language%29)等较早的学习编码系统。 屏幕在右侧的代码编辑器和左侧的迷宫之间划分。 迷宫内有一个化身，玩家可以使用一组受限制的命令（例如`self.moveDown()` ， `self.moveRight()` ， `self.attack(self.findNearestEnemy())`等）来控制化身。 必须正确键入命令来控制虚拟形象，带有逻辑错误的错误程序（例如命令虚拟形象在墙上运行）将导致其失去生命值并最终死亡。

在每个关卡中，为玩家分配一组任务-通常是收集宝石，打败怪物并移至关卡的出口。 播放器逐渐被引入到新命令中，例如循环，条件和变量。 在一个关卡中收集的钻石可以在关卡之间进行投资，以获得更好的装甲，武器和编程命令（巧妙地表示为拼写本和魔法设备），以掌握更高级别的棘手任务。

CodeCombat从流畅的学习曲线开始，非常适合没有编码经验的玩家。 随着玩家的进步，任务涉及更复杂的编程概念。 最重要的是，关卡本身由于与游戏世界中的对象进行更多可能的交互而变得更加复杂：可以建立围栏，可以设置火圈，可以将敌人引诱到雷区中，使用特殊武器可以使用冷却时间计时器进行特殊攻击，等等

除了设计精美的关卡外，游戏的后期阶段还具有许多谜题，这些谜题足以吸引游戏玩家和编码人员。

**执照**

可以在[MIT](https://en.wikipedia.org/wiki/MIT_License)的免费[许可证](https://en.wikipedia.org/wiki/MIT_License)下在GitHub上找到*CodeCombat*本身。 所有艺术资产（精灵，背景，声音效果等）也可以在GitHub上找到，并根据Creative Commons [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)许可发布。 这样可以轻松地将游戏插图用于学生的项目。

**商业模式**

许可和归属在[CodeCombat法律页面](http://codecombat.com/legal)上有更详细的说明。 CodeCombat保留发布使用非免费许可证使用CodeCombat级别编辑器创建和上传的CodeCombat的级别的权利。

当前的商业模式依靠“诱使”父母和老师加入每月9.99美元的订阅中，以访问视频教程，更多级别和更多（虚拟）钻石。 尽管内置的广告和订阅功能可能会有些刺激，但这是围绕免费/自由/开源核心构建业务生态系统的合法方法。

因为完整的CodeCombat源代码位于GitHub上，所以分叉者可以创建自己的代码战斗系统，并附加不同的业务模型（或根本没有业务模型）。

**用户参与**

CodeCombat寻求用户对关卡设计，编码，翻译和其他任务的贡献。 我特别期待教师和教育工作者从社区创建的内容，例如用于将CodeCombat课程整合到计算机科学课程中的课程计划或最佳实践指南。

<sup>屏幕快照由Horst Jens提供。</sup> <sup>[CC BY-SA 4.0](https://creativecommons.org/licenses/by/4.0/) 。</sup>

**教学经验**

我自己在编程课程中使用CodeCombat的经历很愉快。 我11岁的学生受到CodeCombat的欢迎，并且经常吸引愿意“帮助”的年龄较大的学生。 学生几乎不需要老师的帮助就可以自己解决大部分任务。 对于某些级别，任务描述隐藏在代码注释中。 在较高的水平上，我的说德语的学生英语水平有限是一个问题。

游戏化效果很好，尤其是在年轻学生中。 他们喜欢花时间思考如何最好地投资来之不易的虚拟钻石，当他们获得优质的虚拟装甲和武器时，他们感到非常高兴。

**批判**

我没有什么可批评的，但有几件事：

*   *   **[Python的](http://docs.python-guide.org/en/latest/writing/style/)非蟒：CodeCombat**学生学到很多东西，只有在游戏世界中存在的命令。 尽管这在游戏中很好，但是某些“结构”命令（例如`loop:`可以很容易地由正确的Python命令（ `while True:` ：）代替。
    *   **[强制面向对象](https://en.wikipedia.org/wiki/Object-oriented_programming) ：** CodeCombat在开始时引入了诸如`self.moveDown()`而不是`moveDown()`类的命令，指示该头像是头像类的实例。 虽然我喜欢从一开始就做正确的概念并在以后进行解释，但我想知道是否真的有必要在无需对象的情况下很好地教授必要的教学（循环，条件，变量），立即将面向对象的概念强加给学生取向范式。 我想这是为了使CodeCombat能够使用其他编程语言，例如Java。

* * *

## 密码战

Codewars是CodeCombat的更成熟的版本。 学生并没有经过课程指导，而是面对编程任务-与典型的计算机科学班的家庭作业不同。

**ata田**

每个编程任务都参考称为[Kata](https://en.wikipedia.org/wiki/Kata)的日本武术。 它们包括简短的任务描述，一组输入数据和所需的输出数据。 学生的任务是用自己喜欢的编程语言编写一个函数，以将给定的输入转换为所需的输出。 所有这些都是通过在线内置编程编辑器完成的。

还要求学生编写自己的测试，测试的结果（通过或失败）提供有关代码是否准备好向公众提交的线索。 为了使Katas更加困难，任务描述中给定的一组输入-输出数据只是在将Kata提交给公众之前用于测试Kata的数据的子集。 用户可以使用按钮针对自己的测试运行其功能，也可以按“提交”以针对更大的隐藏数据集进行测试。 只有通过所有测试后，该功能才能上载并由公众检查。

这是一个非常具有启示意义的时刻：即使对于一个看似简单的问题，也存在无数种不同的解决方案。 可以将解决方案称为“最佳实践”，以便所有编码人员的群策群力将最可接受的解决方案排在首位。 也可以将解决方案投票为“聪明”。

还有一个内置的网络论坛，可以讨论Kata解决方案。

Codewars中的游戏化程度不高，但是解决Katas以及其他一些活动将慢慢提高学生的排名。

<sup>屏幕快照由Horst Jens提供。</sup> <sup>[CC BY-SA 4.0](https://creativecommons.org/licenses/by/4.0/) 。</sup>

**库米特**

与Katas相比，Kumites更为先进，它是更为复杂的编码问题，邀请其他编码人员重构代码并提供解决方案。

**教学经验与批评**

虽然我个人喜欢Codewars，但我发现它对教授Python并不理想（我在14岁的德语德语学生中进行了测试，他们具有一些Python知识和英语基础知识）。 与CodeCombat相比，教学必须在使用Codewars之前进行，否则学生必须具有技能和自律才能以其他方式学习必要的编码技能。

最大的问题是理解任务描述和理解如何使用编写测试。 简而言之，大多数测试使用assert.equal语句：

`Test.assert_equals(function_name('input data'),'desired output data')`

不幸的是，这条线并未在所有Katas的测试区域中出现，这进一步使学生感到困惑。

但是，Codewars通过查看（并讨论）其他解决方案提供了巨大的学习机会。 这也是用另一种新的编程语言处理已经在首选编程语言中解决的Katas的好工具。

最后，Codewars非常适合通过编码dojos来引入结[对编程](https://en.wikipedia.org/wiki/Pair_programming)的概念：两个学生必须一起解决一个问题，其中一个要进行思考（导航），而另一个要进行打字（驱动）。 在给定的时间间隔后或至少通过一项测试后，新学生将成为驾驶员，驾驶员将成为导航员。

**参与和执照**

鼓励Codewars用户参加。 内置了讨论，共享和分叉Katas和Kumites的功能。 如Codewars条款页面中所述，所有上载的代码均根据[FreeBSD 2-Clause许可获得许可](http://opensource.org/licenses/BSD-2-Clause) 。

**商业模式**

目前尚不清楚Codewars的商业模式是什么。 我认为该站点可以用作IT工作的招聘工具，但我希望该站点能够吸引像我这样感恩的计算机科学老师的足够捐助，他们终于摆脱了创建和评分作业的需要。

*最初发布在[spielend-programmieren.at上](http://spielend-programmieren.at/blog/20150702_codewarscodecombat.html) 。* *经知识共享许可，重新发布。*

> 翻译自: [https://opensource.com/education/15/7/codewars-codecombat-review](https://opensource.com/education/15/7/codewars-codecombat-review)

4:2:0编码