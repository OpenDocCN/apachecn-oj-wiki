<!--yml
category: codewars
date: 2022-08-13 11:44:09
-->

# codewars： Don't rely on luck._毕竟是孩子啊的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36984080/article/details/87790535?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-87790535.nonecase](https://blog.csdn.net/qq_36984080/article/details/87790535?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-87790535.nonecase)

Instructions:

The test fixture I use for this kata is pre-populated.
It will compare your guess to a random number generated using:
    rand(1, 100)
You can pass by relying on luck or skill but try not to rely on luck.
"The power to define the situation is the ultimate power." - Jerry Rubin
Good luck!

```
Solution:

    //方案1:初始化随机数。
    srand(0);
    $guess = rand(1,100);
    srand(0);

    //方案2:
    $guess = true;

Sample Tests:

    class DontRelyOnLuckKata extends TestCase
    {
        //This is exactly what the real test fixture looks like.
        public function testYourLuck() {
          global $guess;
          $lucky_number = rand(1, 100);
          $this->assertEquals($lucky_number, $guess, "Sorry. Unlucky this time.");
        }
    }
```