<!--yml
category: codewars
date: 2022-08-13 11:32:36
-->

# [Codewar训练]Codewars Style Ranking System（CodeWars头衔系统）_qq_28033719的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_28033719/article/details/105640049?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-105640049.142^v40^control,185^v2^control](https://blog.csdn.net/qq_28033719/article/details/105640049?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-105640049.142^v40^control,185^v2^control)

### 问题：

段位：4

说明：

具体还是丢翻译吧，头衔制度是分为 -8 ~ 8，没有 0 等级。每100经验升1级，-1 升级之后是 1。

用户进行活动，活动等级如果小于用户等级 1 以上就没有得分，少于 1 得 1分，相等 3 分，超过 n 级10 * n * n分

头衔规则（原文）：

```
Business Rules:
A user starts at rank -8 and can progress all the way to 8.
There is no 0 (zero) rank. The next rank after -1 is 1.
Users will complete activities. These activities also have ranks.
Each time the user completes a ranked activity the users rank progress is updated based off of the activity's rank
The progress earned from the completed activity is relative to what the user's current rank is compared to the rank of the activity
A user's rank progress starts off at zero, each time the progress reaches 100 the user's rank is upgraded to the next level
Any remaining progress earned while in the previous rank will be applied towards the next rank's progress (we don't throw any progress away). The exception is if there is no other rank left to progress towards (Once you reach rank 8 there is no more progression).
A user cannot progress beyond rank 8.
The only acceptable range of rank values is -8,-7,-6,-5,-4,-3,-2,-1,1,2,3,4,5,6,7,8\. Any other value should raise an error.
The progress is scored like so:

Completing an activity that is ranked the same as that of the user's will be worth 3 points
Completing an activity that is ranked one ranking lower than the user's will be worth 1 point
Any activities completed that are ranking 2 levels or more lower than the user's ranking will be ignored
Completing an activity ranked higher than the current user's rank will accelerate the rank progression. The greater the difference between rankings the more the progression will be increased. The formula is 10 * d * d where d equals the difference in ranking between the activity and the user.
Logic Examples:
If a user ranked -8 completes an activity ranked -7 they will receive 10 progress
If a user ranked -8 completes an activity ranked -6 they will receive 40 progress
If a user ranked -8 completes an activity ranked -5 they will receive 90 progress
If a user ranked -8 completes an activity ranked -4 they will receive 160 progress, resulting in the user being upgraded to rank -7 and having earned 60 progress towards their next rank
If a user ranked -1 completes an activity ranked 1 they will receive 10 progress (remember, zero rank is ignored)
```

输入输出案例：

```
User user = new Codewarsstylerankingsystem().new User();
System.out.println(user.rank); // => -8
System.out.println(user.progress); // => 0
user.incProgress(-7);
System.out.println(user.progress); // => 10
user.incProgress(-5); // will add 90 progress
System.out.println(user.progress); // => 0 // progress is now zero
System.out.println(user.rank); // => -7 // ra
```

### 我的代码：

主要是incProgress写写升级算法，其他的没有了，说好不算好，有一点代码量

```
public class Codewarsstylerankingsystem {

    public static void main(String[] args) {
        User user = new Codewarsstylerankingsystem().new User();
        System.out.println(user.rank); // => -8
        System.out.println(user.progress); // => 0
        user.incProgress(-7);
        System.out.println(user.progress); // => 10
        user.incProgress(-5); // will add 90 progress
        System.out.println(user.progress); // => 0 // progress is now zero
        System.out.println(user.rank); // => -7 // ra
    }

    // 原题只要你写User类，其他的都是多余的
    class User {
        public int rank = -8;
        public int progress = 0;
        private int[] pros = new int[]{1, 3, 10};

        public void incProgress(int rank) {
            // 超头衔就抛出异常
            if(rank < -8 || rank == 0 || rank > 8) throw new IllegalArgumentException();

            // 这里主要是把 -1 和 1 的区间合并，所以 - 1
            if(rank > 0) rank -= 1;
            int temp = this.rank;
            if(temp > 0) temp -= 1;
            if(rank < temp - 1) return;

            // dis记录pros[]数组的位置对应奖励
            int dis = rank - temp + 1;
            // d是活动等级和等级的距离
            int d = 1;
            if(dis > 1) {
                d = dis - 1;
                dis = 2;
            }

            progress += pros[dis] * d * d;

            // 如果发现进度超过100，进行行升级
            if(progress >= 100) {
                // temp记录了rank合并值，pos则是升级后位置，不能超过 7
                int pos = temp + progress / 100;
                temp = pos > 7 ? 7 : pos;

                // 进行升级之后，发现>= 0的都需要提升 1 级，因为上面合并了
                if(temp >= 0) this.rank = temp + 1;
                else this.rank = temp;
            }

            // 如果等级8，进度为0
            if(this.rank == 8) progress = 0;
            else progress %= 100;
        }
    }
} 
```