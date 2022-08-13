<!--yml
category: codewars
date: 2022-08-13 11:41:04
-->

# codewars -The Greatest Warrior_德华的神兜兜的博客-CSDN博客

> 来源：[https://blog.csdn.net/anbncn1234/article/details/104677274?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-104677274.142^v40^control,185^v2^control](https://blog.csdn.net/anbncn1234/article/details/104677274?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-104677274.142^v40^control,185^v2^control)

codewars -The Greatest Warrior
代码：

执行报错，不知道还有哪些条件没有写出来， 题目太长看不下去了

```
class Warrior():
    ex = 100
    rank1 = ["Pushover", "Novice", "Fighter", "Warrior", "Veteran", "Sage", "Elite", "Conqueror", "Champion", "Master", "Greatest"]
    att = []
    def experience(self):

        return self.ex
    def level(self):
        level = self.ex // 100

        return level
    def rank(self):
        index = self.ex // 1000

        return self.rank1[index]
    def achievements(self):

        return self.att
    def training(self, traininglist):

        if self.level()>=traininglist[2]:
            self.ex += traininglist[1]
            if self.ex >10000:
                self.ex = 10000
            self.att.append(traininglist[0])
            return traininglist[0]
        else:
            return "Not strong enough"
    def battle(self,enemylevel):
        if enemylevel < 1 or enemylevel >100:
            return "Invalid level"
        enemylevel_rank = self.rank1[enemylevel // 10]

        print(self.rank1.index(enemylevel_rank))
        if self.level() == enemylevel:
            self.ex += 10
            return "A good fight"
        elif self.level() - enemylevel == 1:
            self.ex += 5
            return "A good fight"
        elif self.level() - enemylevel >= 2:
            return "Easy fight"
        elif enemylevel - self.level() > 5 or self.rank1.index(enemylevel_rank) > self.rank1.index(self.rank()):
            return "You've been defeated"
        elif 1< enemylevel - self.level() < 5 :
            self.ex += 20 *(enemylevel - self.level())*(enemylevel - self.level())
            return "An intense fight"
        if self.ex > 10000:
            self.ex = 10000 
```