<!--yml
category: codewars
date: 2022-08-13 11:50:00
-->

# Codewars : Take a Ten Minute Walk（步行十分钟）_桃陉的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_46308081/article/details/113831595?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-113831595.nonecase](https://blog.csdn.net/weixin_46308081/article/details/113831595?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-113831595.nonecase)

`纪念第一次刷Codewars`

## 1.问题描述

`原题`：

∙ \bullet ∙ You live in the city of Cartesia where all roads are laid out in a perfect grid. You arrived ten minutes too early to an appointment, so you decided to take the opportunity to go for a short walk. The city provides its citizens with a Walk Generating App on their phones – everytime you press the button it sends you an array of one-letter strings representing directions to walk (eg. [‘n’, ‘s’, ‘w’, ‘e’]). You always walk only a single block for each letter (direction) and you know it takes you one minute to traverse one city block, so create a function that will return true if the walk the app gives you will take you exactly ten minutes (you don’t want to be early or late!) and will, of course, return you to your starting point. Return false otherwise.

∙ \bullet ∙ `Note`: you will always receive a valid array containing a random assortment of direction letters (‘n’, ‘s’, ‘e’, or ‘w’ only). It will never give you an empty array (that’s not a walk, that’s standing still!).

* * *

`翻译`：

∙ \bullet ∙ 您住在笛卡尔市，那里的所有道路都以完美的网格布局。您提前十分钟到达预约地点，所以您决定趁机散步。该城市在其手机上为市民提供了一个“步行生成”应用程序-每次您按下按钮时，都会向您发送一个由一个字母组成的字符串数组，这些字符串代表行走的方向（例如[‘n’，‘s’，‘w’， ‘e’]）。您总是每个字母（方向）只走一个街区，并且知道走过一个城市街区要花费一分钟，因此创建一个函数，如果应用程序给您走，它将返回true，而该函数将花费您正好十分钟（不想早或晚！），当然，它将使您回到起点。否则返回false。

∙ \bullet ∙ `注意`：您将始终收到一个有效的数组，其中包含方向字母的随机分类（仅’n’，‘s’，‘e’或’w’）。它永远不会给您一个空数组（这不是步行，而是停滞不前！）。

难 度 ： 6 k y u {\color{Purple} 难度：6kyu} 难度：6kyu

* * *

## 2.问题分析

∙ \bullet ∙ `题目重述`：给定一个数组，其中有四个方向的走向，当你走十次并刚好走回原点时，返回true，否则返回false。

∙ \bullet ∙ `思路`：首先判断是否走十分钟。然后分别考虑每个方向，用x来控制左右方向，向左走加1，向右走减1；用y来控制上下方向，向上走加1，向下走减1。初始化 x = 0 , y = 0 , x=0,y=0, x=0,y=0,最后看x和y是否仍然等于0。

∙ \bullet ∙ `优化`：使用一些特定的函数可以使算法更加的简便。

* * *

## 3.代码

∙ \bullet ∙ `普通做法`:

```
#include<vector>
bool isValidWalk(std::vector<char> walk) {
  	if(walk.size() != 10) return false;
  	int x=0, y=0;
  	for(char c : walk){
    	switch(c) {
      		case 'n': y++; break;
      		case 's': y--; break;
      		case 'e': x++; break;
      		case 'w': x--; break;
    	}
  	}
  	if(x == 0 && y == 0) return true;
  	return false;
} 
```

∙ \bullet ∙ `使用函数`:

```
#include<vector>
#include <algorithm> 

bool isValidWalk(std::vector<char> walk) {
  return walk.size() == 10 && 
         std::count(walk.begin(), walk.end(), 'e') == std::count(walk.begin(), walk.end(), 'w') &&
         std::count(walk.begin(), walk.end(), 'n') == std::count(walk.begin(), walk.end(), 's');
} 
```