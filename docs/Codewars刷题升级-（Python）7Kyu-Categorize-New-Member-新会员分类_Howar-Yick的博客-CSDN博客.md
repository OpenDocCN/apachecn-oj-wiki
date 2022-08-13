<!--yml
category: codewars
date: 2022-08-13 11:49:30
-->

# Codewars刷题升级 （Python）7Kyu Categorize New Member 新会员分类_Howar Yick的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41432655/article/details/90693575?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-90693575.nonecase](https://blog.csdn.net/weixin_41432655/article/details/90693575?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-90693575.nonecase)

**题目描述：**

> The Western Suburbs Croquet Club has two categories of membership, Senior and Open. They would like your help with an application form that will tell prospective members which category they will be placed.
> 西郊槌球俱乐部有两类会员，即高级和公开会员。他们希望您提供申请表格的帮助，告诉潜在会员他们将被安排哪个类别
> 
> To be a senior, a member must be at least 55 years old and have a handicap greater than 7\. In this croquet club, handicaps range from -2 to +26; the better the player the lower the handicap.
> 成为高级会员，成员必须年满55岁，并且有一个大于7的差点。在这个槌球俱乐部，差点从-2到+26;玩家越好差点越低。

**Input
输入**

> Input will consist of a list of lists containing two items each. Each list contains information for a single potential member. Information consists of an integer for the person’s age and an integer for the person’s handicap.
> Note for F#: The input will be of (int list list) which is a List
> 输入将包含一个列表，每个列表包含两个项目。每个列表包含单个潜在成员的信息。信息包括人的年龄的整数和人的差点的整数。

****Example Input**
样例输入：**

> [[18, 20],[45, 2],[61, 12],[37, 6],[21, 21],[78, 9]]

**Output
输出：**

> Output will consist of a list of string values stating whether the respective member is to be placed in the senior or open category.
> 输出将包含一个字符串值列表，说明相应的成员是高级还是公开类别中。

**Example Output
样例输出：**

> [“Open”, “Open”, “Senior”, “Open”, “Open”, “Senior”]

**解题思路：**
简单迭代输入列表，判断条件即可。

**代码实现：**

```
def openOrSenior(data):
    # Hmmm.. Where to start?
    result=[]
    for _ in data:
        if _[0]>=55 and _[1]>7:
            result.append('Senior')
        else:
            result.append('Open')
    return result 
```