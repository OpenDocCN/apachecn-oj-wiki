<!--yml
category: codewars
date: 2022-08-13 11:40:09
-->

# 【codewars-18】弹跳球_Salted_Sun的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42338512/article/details/123916508?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-9-123916508-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_42338512/article/details/123916508?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-9-123916508-null-null.142^v40^control,185^v2^control&utm_term=codewars)

A child is playing with a ball on the nth floor of a tall building. The height of this floor, h, is known.

He drops the ball out of the window. The ball bounces (for example), to two-thirds of its height (a bounce of 0.66).

His mother looks out of a window 1.5 meters from the ground.

How many times will the mother see the ball pass in front of her window (including when it’s falling and bouncing?

**Three conditions** must be met for a valid experiment:
Float parameter “h” in meters must be greater than 0
Float parameter “bounce” must be greater than 0 and less than 1
Float parameter “window” must be less than h.
If all three conditions above are fulfilled, return a positive integer, otherwise return -1.

Note:
The ball can only be seen if the height of the rebounding ball is strictly greater than the window parameter.

Examples:

```
- h = 3, bounce = 0.66, window = 1.5, result is 3

- h = 3, bounce = 1, window = 1.5, result is -1 
```

**分析**

以一次高于window的下落和随后的反弹作为一次循环. 每次循环更新一次cur, 作为一次下落+回弹后那一瞬间的高度.
这样一次循环至少增加一次count, 因为高于window的下落至少会贡献一次; 只要反弹后的高度> window,那么意味着两件事情:

1.  count在本次循环中要增加2
2.  循环还会有下一次.

反之, 若反弹后的高度cur < window, 则有:

1.  count只会增加一次.
2.  这将是最后一次循环.

```
class Bouncingball
{
public:
    static int bouncingBall(double h, double bounce, double window){
      if(h <= 0 || bounce <=0 || bounce >=1 || window >= h){
        return -1;
      } 
     int count{0};
     double cur{h};
      while(cur > window) {
        cur = cur*bounce ;
        count += (cur>window)? 2 :1 ;
      }
      return count;
    }
}; 
```