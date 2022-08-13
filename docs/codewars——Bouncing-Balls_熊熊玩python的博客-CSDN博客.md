<!--yml
category: codewars
date: 2022-08-13 11:32:25
-->

# codewars——Bouncing Balls_熊熊玩python的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41552148/article/details/100132650?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-100132650.142^v40^control,185^v2^control](https://blog.csdn.net/weixin_41552148/article/details/100132650?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-100132650.142^v40^control,185^v2^control)

> A child is playing with a ball on the nth floor of a tall building. The height of this floor, h, is known.He drops the ball out of the window. The ball bounces (for example), to two-thirds of its height (a bounce of 0.66).His mother looks out of a window 1.5 meters from the ground.How many times will the mother see the ball pass in front of her window (including when it’s falling and bouncing?Three conditions must be met for a valid experiment:Float parameter “h” in meters must be greater than 0Float parameter “bounce” must be greater than 0 and less than 1Float parameter “window” must be less than h.If all three conditions above are fulfilled, return a positive integer, otherwise return -1.Note:The ball can only be seen if the height of the rebounding ball is stricty greater than the window parameter.

> /*
> 一个孩子在一栋高楼的第N层玩球。这层楼的高度h是已知的。
> 他把球从窗口扔了出去。球反弹（例如）到其高度的三分之二（反弹0.66）。
> 他母亲从离地1.5米的窗户向外看。
> 妈妈会看到球在她窗前经过多少次（包括什么时候落下和弹跳）？
> 有效实验必须满足三个条件：
> 以米为单位的浮点参数“h”必须大于0
> 浮动参数“bounce”必须大于0且小于1
> 浮动参数“window”必须小于h。
> 如果满足上述三个条件，则返回正整数，否则返回-1。
> 注：
> 只有篮板球的高度比窗口参数严格时，才能看到球。
> */

```
#include <iostream>
using namespace std;
class Bouncingball
{
public:
    static int bouncingBall(double h, double bounce, double window);
};
int Bouncingball::bouncingBall(double h, double bounce, double window)
{
    int count = 0;
    if (h <= 0 || bounce >= 1 || bounce <= 0 || window >= h)
    {
        return -1;
    }
    if (h >= window)
        count += 1;
    while (true)
    {
        h *= bounce;
        if (h > window)
            count += 2;
        else
            break;
    }
    return count;
}

int main()
{
    Bouncingball ball;
    cout << ball.bouncingBall(30, 0.66, 1.5);
    return 0;
} 
```

# 总结

用了循环，一开始一直想用递归方法，陷入怪圈