<!--yml
category: 蓝桥杯
date: 2022-04-26 11:07:20
-->

# 2018年第九届蓝桥杯省赛试题及详解（Java高职高专C组）_跟老程一起学编程的博客-CSDN博客

> 来源：[https://blog.csdn.net/future277809183/article/details/123162262](https://blog.csdn.net/future277809183/article/details/123162262)

[【蓝桥杯】历年真题题目及题解汇总](https://blog.csdn.net/future277809183/article/details/122826573 "【蓝桥杯】历年真题题目及题解汇总")

* * *

1.  结果填空 (满分3分)
2.  结果填空 (满分5分)
3.  结果填空 (满分9分)
4.  代码填空 (满分11分)
5.  代码填空 (满分13分)
6.  结果填空 (满分15分)
7.  结果填空 (满分19分)
8.  程序设计（满分21分）
9.  程序设计（满分23分）
10.  程序设计（满分31分）

* * *

## 第一题：哪天返回

小明被不明势力劫持。后被扔到x星站再无问津。小明得知每天都有飞船飞往地球，但需要108元的船票，而他却身无分文。
他决定在x星战打工。好心的老板答应包食宿，第1天给他1元钱。
并且，以后的每一天都比前一天多2元钱，直到他有足够的钱买票。
请计算一下，小明在第几天就能凑够108元，返回地球
**答案：11**

```
public class Main{
    public static void main(String[] args) {
        int salary = 1; // 每天的工资
        int money = 0; // 小明身上的钱
        int i;
        for (i = 0; money < 108; i++) {
            money += salary;
            salary += 2;
        }
        System.out.println(i);
    }
}
```

## **第二题：猴子分香蕉**

5只猴子是好朋友，在海边的椰子树上睡着了。这期间，有商船把一大堆香蕉忘记在沙滩上离去。
第1只猴子醒来，把香蕉均分成5堆，还剩下1个，就吃掉并把自己的一份藏起来继续睡觉。
第2只猴子醒来，重新把香蕉均分成5堆，还剩下2个，就吃掉并把自己的一份藏起来继续睡觉。
第3只猴子醒来，重新把香蕉均分成5堆，还剩下3个，就吃掉并把自己的一份藏起来继续睡觉。
第4只猴子醒来，重新把香蕉均分成5堆，还剩下4个，就吃掉并把自己的一份藏起来继续睡觉。
第5只猴子醒来，重新把香蕉均分成5堆，哈哈，正好不剩！

请计算一开始最少有多少个香蕉。
**答案：3141**

```
public class Main{
    public static void main(String[] args) {
        for (int i = 20; i < 10000; i++) {
            float f = (float) i;
            for (int j = 1; j <= 4; j++) {
                // j是被猴子吃掉的,(f-j)/(float)(5.0)是被猴子藏起来的香蕉
                f = f - j - (f - j) / (float) (5.0);
            }
            if (f % 5 == 0) {
                System.out.println(i);
                break;
            }
        }
    }

}
```

## **第三题：字母阵列**

仔细寻找，会发现：在下面的8x8的方阵中，隐藏着字母序列："LANQIAO"。
SLANQIAO
ZOEXCCGB
MOAYWKHI
BCCIPLJQ
SLANQIAO
RSFWFNYA
XIFZVWAL
COAIQNAL

我们约定: 序列可以水平，垂直，或者是斜向；
并且走向不限（实际上就是有一共8种方向）。
上图中一共有4个满足要求的串。

下面有一个更大的（100x100）的字母方阵。
你能算出其中隐藏了多少个“LANQIAO”吗？
题目太长我就不上了,测试数据可以用这个短的
**答案：41**

```
import java.util.Scanner;

public class Main{
    static Scanner sc = new Scanner(System.in);
    //往8个方向移动
    static int[][] move = { { -1, -1 }, { -1, 0 }, { -1, 1 }, { 0, 1 }, { 1, 1 }, { 1, 0 }, { 1, -1 }, { 0, -1 } };
    static char[][] map = new char[100][100];
    static String LQ = "LANQIAO";
    static int cnt = 0;

    public static void main(String[] args) {
        for (int i = 0; i < 100; i++) {
            map[i] = sc.next().toCharArray();
        }
        for (int i = 0; i < 100; i++) {
            for (int j = 0; j < 100; j++) {
                //是L才搜索8个方向
                if(map[i][j] == 'L') {
                    //8个方向
                    for (int j2 = 0; j2 < move.length; j2++) {
                        int x = i;
                        int y = j;
                        String str = "L";
                        //7个字符
                        for (int k = 1; k < LQ.length(); k++) {
                            x += move[j2][0];
                            y += move[j2][1];
                            //判断是否越界和是否是LANQIAO中的任意字符
                            if(x<0 || x>=100 || y <0 || y>=100 || LQ.indexOf(map[x][y]) == -1) {
                                break;
                            }
                            str+=map[x][y];
                        }
                        if(str.equals(LQ)) {
                            cnt++;
                        }
                    }
                }
            }
        }
        System.out.println(cnt);
    }
}
```

## **第四题：第几个幸运数**

到x星球旅行的游客都被发给一个整数，作为游客编号。
x星的国王有个怪癖，他只喜欢数字3,5和7。
国王规定，游客的编号如果只含有因子：3,5,7,就可以获得一份奖品。

我们来看前10个幸运数字是：
3 5 7 9 15 21 25 27 35 45
因而第11个幸运数字是：49

小明领到了一个幸运数字 59084709587505，他去领奖的时候，人家要求他准确地说出这是第几个幸运数字，否则领不到奖品。

请你帮小明计算一下，59084709587505是第几个幸运数字。
**答案：1905**

```
 //第几个幸运数
public class Main {
	public static void main(String[] args) {
		// 记录下标
		int num = 0;
		long a = 59084709587505l;
		// 3的所有次方
		for (int i = 0; a>Math.pow(3, i); i++) {
			// 5的所有次方  3的i次方
			for (int j = 0; a> Math.pow(5, j); j++) {
				// 7的所有次方 5的j次方
				for (int k = 0;  Math.pow(7, k)<a; k++) {
					// 判断数字因子是否为3，5，7  7的k次方
					if (Math.pow(3, i) * Math.pow(5, j) * Math.pow(7, k) < a) {
						num++;

					}

				}
			}
		}
		System.out.println(num);
	}

} 
```

## **第五题：书号验证**

2004年起，国际ISBN中心出版了《13位国际标准书号指南》。
原有10位书号前加978作为商品分类标识；校验规则也改变。
校验位的加权算法与10位ISBN的算法不同，具体算法是：
用1分别乘ISBN的前12位中的奇数位（从左边开始数起），用3乘以偶数位，乘积之和以10为模，10与模值的差值再对10取模（即取个位的数字）即可得到校验位的值，其值范围应该为0~9。

下面的程序实现了该算法，请仔细阅读源码，填写缺失的部分。

```
public class Demo05 {
    static boolean f(String s){
        int k=1;
        int sum = 0;
        for(int i=0; i<s.length(); i++){
            char c = s.charAt(i);
            if(c=='-' || c==' ') continue;
            sum += ___________;  //填空
            k++;
            if(k>12) break; 
        }

        return s.charAt(s.length()-1)-'0' == (10-sum % 10)%10;
    }

    public static void main(String[] args){
        System.out.println(f("978-7-301-04815-3"));
        System.out.println(f("978-7-115-38821-6"));
    }
}
```

```
答案：(c - '0') * (k % 2 == 0?3:1)
```

## **第六题：打印大X**

如下的程序目的是在控制台打印输出大X。
可以控制两个参数：图形的高度，以及笔宽。

用程序中的测试数据输出效果：
(如果显示有问题，可以参看p1.png)

高度=15, 笔宽=3
***           ***
 ***         ***
  ***       ***
   ***     ***
    ***   ***
     *** ***
      *****
       ***
      *****
     *** ***
    ***   ***
   ***     ***
  ***       ***
 ***         ***
***           ***
高度=8, 笔宽=5
*****  *****
 **********
  ********
   ******
   ******
  ********
 **********
*****  *****

请仔细分析程序流程，填写缺失的代码。

```
public class Demo06 {

    static void f(int h, int w){
        System.out.println(String.format("高度=%d, 笔宽=%d",h,w));
        int a1 = 0;
        int a2 = h - 1;

        for(int k=0; k<h; k++){
            int p = Math.min(a1,a2);
            int q = Math.max(a1+w,a2+w);

            for(int i=0; i<p; i++) System.out.print(" ");

            if(q-p<w*2){
               _______________________________________; //填空
            }
            else{
                for(int i=0; i<w; i++) System.out.print("*");
                for(int i=0; i<q-p-w*2; i++) System.out.print(" ");
                for(int i=0; i<w; i++) System.out.print("*");
            }
            System.out.println();
            a1++;
            a2--;
        }
    }

    public static void main(String[] args){
        f(15,3);
        f(8,5);
    }
}
```

```
答案：for(int i=0; i < q-p; i++) System.out.print("*")
```

## **第七题：缩位求和**

在电子计算机普及以前，人们经常用一个粗略的方法来验算四则运算是否正确。
比如：248 * 15 = 3720
把乘数和被乘数分别逐位求和，如果是多位数再逐位求和，直到是1位数，得
2 + 4 + 8 = 14 ==> 1 + 4 = 5;
1 + 5 = 6
5 * 6
而结果逐位求和为 3
5 * 6 的结果逐位求和与3符合，说明正确的可能性很大！！（不能排除错误）

请你写一个计算机程序，对给定的字符串逐位求和：
输入为一个由数字组成的串，表示n位数(n<1000);
输出为一位数，表示反复逐位求和的结果。

例如：
输入：
35379

程序应该输出：
9

再例如：
输入：
7583676109608471656473500295825

程序应该输出：
1

资源约定：
峰值内存消耗（含虚拟机） < 256M
CPU消耗  < 1000ms

请严格按要求输出，不要画蛇添足地打印类似：“请您输入...” 的多余内容。

所有代码放在同一个源文件中，调试通过后，拷贝提交该源码。
不要使用package语句。不要使用jdk1.7及以上版本的特性。
主类的名字必须是：Main，否则按无效代码处理。

```
import java.util.Scanner;

public class Main {
    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {
        char[] ch = sc.next().toCharArray();
        while (true) {
            int sum = 0;
            for (int i = 0; i < ch.length; i++) {
                sum += ch[i] - '0';
            }
            ch = String.valueOf(sum).toCharArray();
            if(ch.length == 1) {
                System.out.println(ch);
                break;
            }
        }
    }

}
```

## **第八题：等腰三角形**

本题目要求你在控制台输出一个由数字组成的等腰三角形。
具体的步骤是：
1\. 先用1,2,3，...的自然数拼一个足够长的串
2\. 用这个串填充三角形的三条边。从上方顶点开始，逆时针填充。
比如，当三角形高度是8时：

       1
      2 1
     3   8
    4     1
   5       7
  6         1
 7           6
891011121314151

输入，一个正整数n(3<n<300),表示三角形的高度
输出，用数字填充的等腰三角形。

为了便于测评，我们要求空格一律用"."代替。

例如：
输入：
5

程序应该输出：
....1
...2.1
..3...2
.4.....1
567891011

再例如：
输入：
10

程序应该输出：
.........1
........2.2
.......3...2
......4.....2
.....5.......1
....6.........2
...7...........0
..8.............2
.9...............9
1011121314151617181

再例如：
输入：
15

程序应该输出：

..............1
.............2.3
............3...2
...........4.....3
..........5.......1
.........6.........3
........7...........0
.......8.............3
......9...............9
.....1.................2
....0...................8
...1.....................2
..1.......................7
.1.........................2
21314151617181920212223242526

资源约定：
峰值内存消耗（含虚拟机） < 256M
CPU消耗  < 1000ms

```
import java.util.Scanner;

public class Main{
    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {
        int n = sc.nextInt();
        // 1+(n-1)*2为底的长度(2*n-3)为两条边减去重合的数字的总长度
        int sum = 1 + (n - 1) * 2 + (2 * n - 3);
        //算出所需要的字符
        String str = "";
        for (int i = 1; str.length() < sum; i++) {
            str += String.valueOf(i);
        }
        char[] ch = str.substring(0, sum).toCharArray();

        // 第一行
        for (int j = 0; j < n - 1; j++) {
            System.out.print(".");
        }
        System.out.println(1);

        // 第二行~第n-1行
        for (int i = 1; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                System.out.print(".");
            }

            System.out.print(ch[i]);

            for (int j = 0; j < i * 2 - 1; j++) {
                System.out.print(".");
            }

            System.out.println(ch[sum - i]);
        }

        //第n行
        for (int i = n - 1; i < sum - n + 2; i++) {
            System.out.print(ch[i]);
        }
    }
}
```

## **第九题：小朋友崇拜圈**

班里N个小朋友，每个人都有自己最崇拜的一个小朋友（也可以是自己）。
在一个游戏中，需要小朋友坐一个圈，
每个小朋友都有自己最崇拜的小朋友在他的右手边。
求满足条件的圈最大多少人？

小朋友编号为1,2,3,...N
输入第一行，一个整数N（3<N<100000）
接下来一行N个整数，由空格分开。

要求输出一个整数，表示满足条件的最大圈的人数。

例如：
输入：
9
3 4 2 5 3 8 4 6 9

则程序应该输出：
4

解释：
如图p1.png所示，崇拜关系用箭头表示，红色表示不在圈中。
显然，最大圈是[2 4 5 3] 构成的圈

再例如：
输入：
30
22 28 16 6 27 21 30 1 29 10 9 14 24 11 7 2 8 5 26 4 12 3 25 18 20 19 23 17 13 15

程序应该输出：
16

资源约定：
峰值内存消耗（含虚拟机） < 256M
CPU消耗  < 1000ms

```
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Main{
    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {
        int n = sc.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }
        int max = 0;
        for (int v : nums) {
            List<Integer> list = new ArrayList<>();
            int cnt = 0;
            int i = v;

            while (!list.contains(i)) {//判断list中有没有这个第i个小朋友
                list.add(i);//添加小朋友崇拜的人
                i = nums[i - 1];//找到当前小朋友崇拜的人
                cnt++;
                if (cnt > max) {
                    max = cnt;
                }
            }
        }
        System.out.println(max);
    }
}
```

## **第十题：耐摔[指数](https://so.csdn.net/so/search?q=%E6%8C%87%E6%95%B0&spm=1001.2101.3001.7020 "指数")(测试次数)**

x星球的居民脾气不太好，但好在他们生气的时候唯一的异常举动是：摔手机。
各大厂商也就纷纷推出各种耐摔型手机。x星球的质监局规定了手机必须经过耐摔测试，并且评定出一个耐摔指数来，之后才允许上市流通。

x星球有很多高耸入云的高塔，刚好可以用来做耐摔测试。塔的每一层高度都是一样的，与地球上稍有不同的是，他们的第一层不是地面，而是相当于我们的2楼。

如果手机从第7层扔下去没摔坏，但第8层摔坏了，则手机耐摔指数=7。
特别地，如果手机从第1层扔下去就坏了，则耐摔指数=0。
如果到了塔的最高层第n层扔没摔坏，则耐摔指数=n

为了减少测试次数，从每个厂家抽样3部手机参加测试。

如果已知了测试塔的高度，并且采用最佳策略，在最坏的运气下最多需要测试多少次才能确定手机的耐摔指数呢？

输入数据，一个整数n（3<n<10000）,表示测试塔的高度。
输出一个整数，表示最多测试多少次。

例如：
输入：
3

程序应该输出：
2

解释：
手机a从2楼扔下去，坏了，就把b手机从1楼扔；否则a手机继续3层扔下

再例如：
输入：
7

程序应该输出：
3

解释：
a手机从4层扔，坏了，则下面有3层，b,c 两部手机2次足可以测出指数；
若是没坏，手机充足，上面5,6,7 三层2次也容易测出。

资源约定：
峰值内存消耗（含虚拟机） < 256M
CPU消耗  < 1000ms

```
import java.util.Scanner;

public class Main{ 
    static Scanner sc = new Scanner(System.in);
    public static void main(String[] args) {
        System.out.println(DroppingPhone(3, sc.nextLong()));  
    }  

    private static long DroppingPhone(long phone, long floors) {  
        long times = 1;  
        while (DroppingMax(phone, times) < floors) {  
            ++times;  
        }  
        return times;  
    }  

    private static long DroppingMax(long phone, long times) {  
        if (phone == 1) {  
            return times;  
        }  

        if (phone >= times) {  
            return (long) Math.pow(2, times) - 1;  
        }  

        return DroppingMax(phone, times - 1) + DroppingMax(phone - 1, times - 1) + 1;  
    }  
} 
```