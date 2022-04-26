<!--yml
category: 蓝桥杯
date: 2022-04-26 11:07:04
-->

# 2016年第七届蓝桥杯省赛试题及详解（Java本科A组）_跟老程一起学编程的博客-CSDN博客

> 来源：[https://blog.csdn.net/future277809183/article/details/122847215](https://blog.csdn.net/future277809183/article/details/122847215)

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

## **第一题：煤球数目**

有一堆煤球，堆成三角棱锥形。具体：
第一层放1个，
第二层3个（排列成三角形），
第三层6个（排列成三角形），
第四层10个（排列成三角形），
....
如果一共有100层，共有多少个煤球？

请填表示煤球总数目的数字。
注意：你提交的应该是一个整数，不要填写任何多余的内容或说明性文字
**答案:171700**

```
 public class Main {
	public static void main(String[] args) {
		int a=1,b=2,sum=1;
		for (int i = 2; i <= 100; i++) {
			sum += (a+b);
			a+=b;
			b++;
		}
		System.out.println(sum);
	}
}

​
```

## **第二题：生日蜡烛**

某君从某年开始每年都举办一次生日party，并且每次都要吹熄与年龄相同根数的蜡烛。

现在算起来，他一共吹熄了236根蜡烛。

请问，他从多少岁开始过生日party的？

请填写他开始过生日party的年龄数。
注意：你提交的应该是一个整数，不要填写任何多余的内容或说明性文字。

答案:26

```
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner in=new Scanner(System.in);
        for(int i=1;i<50;i++) {
        	int sum=0;
        	for(int j=i;j<50;j++) {
        		sum+=j;
        		if(sum==236) {
        			System.out.println(i);
        			j=100;  //退出循环
        			i=100;
        		}else if(sum>236){
        			break;
        		}else {
        			continue;
        		}
        	}
        }
	}
}
```

**第三题：搭积木**

小明最近喜欢搭数字积木，
一共有10块积木，每个积木上有一个数字，0~9。

搭积木规则：
每个积木放到其它两个积木的上面，并且一定比下面的两个积木数字小。
最后搭成4层的金字塔形，必须用完所有的积木。

下面是两种合格的搭法：

   0
  1 2
 3 4 5
6 7 8 9

   0
  3 1
 7 5 2
9 8 6 4    

请你计算这样的搭法一共有多少种？

请填表示总数目的数字。
注意：你提交的应该是一个整数，不要填写任何多余的内容或说明性文字。

**答案:978**

```
import java.util.HashSet;

public class Main {

	public static void main(String[] args) {
		dfs(0);
		System.out.println(ans);
	}
	static HashSet<String> set = new HashSet<>();
	static int[] a = new int[] {0,1,2,3,4,5,6,7,8,9};
	static int ans=0;
	static void dfs(int m) {
		if(m>=10) {
			if(a[0]>=a[1]||a[0]>=a[2])
				return;
			if(a[1]>=a[3]||a[1]>=a[3])
				return;			
			if(a[2]>=a[4]||a[2]>=a[5])
				return;			
			if(a[3]>=a[6]||a[3]>=a[7])
				return;	
			if(a[4]>=a[7]||a[4]>=a[8])
				return;	
			if(a[5]>=a[8]||a[5]>=a[9])
				return;	
			String s="";
			for(int i=0;i<10;i++) {
				s+=a[i];
				System.out.print(a[i]+" ");
			}
			System.out.println();
//			if(!set.contains(s)) {
//				set.add(s);
//				ans++;
//			}
			ans++;
			return;
		}

		for(int i=m;i<10;i++) {
			swap(m,i);
			dfs(m+1);
			swap(m,i);
		}

	}

	static void swap(int i, int j) {
		int t = a[i];
		a[i] = a[j];
		a[j] = t;
	}

}
```

**第四题：分小组**

9名运动员参加比赛，需要分3组进行预赛。
有哪些分组的方案呢？

我们标记运动员为 A,B,C,... I
下面的程序列出了所有的分组方法。

该程序的正常输出为：
ABC DEF GHI
ABC DEG FHI
ABC DEH FGI
ABC DEI FGH
ABC DFG EHI
ABC DFH EGI
ABC DFI EGH
ABC DGH EFI
ABC DGI EFH
ABC DHI EFG
ABC EFG DHI
ABC EFH DGI
ABC EFI DGH
ABC EGH DFI
ABC EGI DFH
ABC EHI DFG
ABC FGH DEI
ABC FGI DEH
ABC FHI DEG
ABC GHI DEF
ABD CEF GHI
ABD CEG FHI
ABD CEH FGI
ABD CEI FGH
ABD CFG EHI
ABD CFH EGI
ABD CFI EGH
ABD CGH EFI
ABD CGI EFH
ABD CHI EFG
ABD EFG CHI
..... (以下省略，总共560行)

```
public class Main {
	public static String remain(int[] a) {
		String s = "";
		for (int i = 0; i < a.length; i++) {
			if (a[i] == 0)
				s += (char) (i + 'A');
		}
		return s;
	}

	public static void f(String s, int[] a) {
		for (int i = 0; i < a.length; i++) {
			if (a[i] == 1)
				continue;
			a[i] = 1;
			for (int j = i + 1; j < a.length; j++) {
				if (a[j] == 1)
					continue;
				a[j] = 1;
				for (int k = j + 1; k < a.length; k++) {
					if (a[k] == 1)
						continue;
					a[k] = 1;
					System.out.println(); // 填空位置
					a[k] = 0;
				}
				a[j] = 0;
			}
			a[i] = 0;
		}
	}

	public static void main(String[] args) {
		int[] a = new int[9];
		a[0] = 1;

		for (int b = 1; b < a.length; b++) {
			a[b] = 1;
			for (int c = b + 1; c < a.length; c++) {
				a[c] = 1;
				String s = "A" + (char) (b + 'A') + (char) (c + 'A');
				f(s, a);
				a[c] = 0;
			}
			a[b] = 0;
		}
	}
}
```

## 第五题：抽签

X星球要派出一个5人组成的观察团前往W星。
其中：
A国最多可以派出4人。
B国最多可以派出2人。
C国最多可以派出2人。
....

那么最终派往W星的观察团会有多少种国别的不同组合呢？

下面的程序解决了这个问题。
数组a[] 中既是每个国家可以派出的最多的名额。
程序执行结果为：
DEFFF
CEFFF
CDFFF
CDEFF
CCFFF
CCEFF
CCDFF
CCDEF
BEFFF
BDFFF
BDEFF
BCFFF
BCEFF
BCDFF
BCDEF
....
(以下省略，总共101行)

```
public class A
{
    public static void f(int[] a, int k, int n, String s)
    {
        if(k==a.length){ 
            if(n==0) System.out.println(s);
            return;
        }

        String s2 = s;
        for(int i=0; i<=a[k]; i++){
            _____________________________;   //填空位置
            s2 += (char)(k+'A');
        }
    }

    public static void main(String[] args)
    {
        int[] a = {4,2,2,1,1,3};

        f(a,0,5,"");
    }
}
```

```
答案： f(a,k+1,n-i,s2);
```

**第六题：寒假作业**

现在小学的数学题目也不是那么好玩的。
看看这个寒假作业：

   □ + □ = □
   □ - □ = □
   □ × □ = □
   □ ÷ □ = □

   (如果显示不出来，可以参见【图1.jpg】)

每个方块代表1~13中的某一个数字，但不能重复。
比如：
 6  + 7 = 13
 9  - 8 = 1
 3  * 4 = 12
 10 / 2 = 5

以及： 
 7  + 6 = 13
 9  - 8 = 1
 3  * 4 = 12
 10 / 2 = 5

就算两种解法。（加法，乘法交换律后算不同的方案）

你一共找到了多少种方案？

请填写表示方案数目的整数。
注意：你提交的应该是一个整数，不要填写任何多余的内容或说明性文字
![](img/274a926fe26ad3d385520dc1f7759adb.png)

**答案：64**

```
public class Main {

	public static void main(String[] args) {
		dfs(0);
		System.out.println(ans);
	}
	static int[] a = new int[] {1,2,3,4,5,6,7,8,9,10,11,12,13};
	static int ans=0;
	static void dfs(int m) {
		if(m>=13) {//+ - * /
			if(a[0]+a[1]==a[2] && a[3]-a[4]==a[5] && a[6]*a[7]==a[8] && a[9]/a[10]==a[11] && a[9]%a[10]==0) {
				if(ans<10) {//11/2==5
				System.out.println(a[0]+"+"+a[1]+"=="+a[2]);
				System.out.println(a[3]+"-"+a[4]+"=="+a[5]);
				System.out.println(a[6]+"*"+a[7]+"=="+a[8]);
				System.out.println(a[9]+"/"+a[10]+"=="+a[11]);
				System.out.println();
				}
				ans++;

			}

			return;
		}
		if(m>=3 && a[0]+a[1]!=a[2])//剪枝,2^13跑不出来
			return;
		if(m>=6 && a[3]-a[4]!=a[5])//这个剪不剪都行反正跑出来了
			return;

		for(int i=m;i<13;i++) {
			swap(m,i);
			dfs(m+1);
			swap(m,i);
		}
	}

	static void swap(int i, int j) {
		int t = a[i];
		a[i] = a[j];
		a[j] = t;
	}

}
```

## **第七题：剪邮票**

如【图1.jpg】, 有12张连在一起的12生肖的邮票。 现在你要从中剪下5张来，要求必须是连着的。 （仅仅连接一个角不算相连）

![](img/e328221275662c1285683a5a78f980ea.png)
比如，【图2.jpg】，【图3.jpg】中，粉红色所示部分就是合格的剪取。 请你计算，一共有多少种不同的剪取方法

![](img/e8980646fce563479ce0983bd177efc9.png)

![](img/bea7fd5ad683535090b94999a4f6c1b8.png)

```
import java.util.Arrays;
import java.util.HashSet;

public class Main{

	public static void main(String[] args) {

		for(int i=1;i<=12;i++) {
			for(int j=i+1;j<=12;j++) {
				for(int k=j+1;k<=12;k++) {
					for(int x=k+1;x<=12;x++) {
						for(int y=x+1;y<=12;y++) {
							vis[i]=vis[j]=vis[k]=vis[x]=vis[y]=true;
							t=0;
							dfs(i);
							if(t==5)
								ans++;
							vis[i]=vis[j]=vis[k]=vis[x]=vis[y]=false;
						}
					}
				}
			}			
		}
		System.out.println(ans);
	}

//	static char[] a = new char[] {'A','B','C','D','E','F','G','H','I','J','K','L'};
//	static HashSet<String> set = new HashSet<>();
	static boolean[] vis = new boolean[13];
	static int ans = 0;
	static int t=0;

	static void dfs(int x) {
		vis[x]=false;
		t++;
		if(x!=1 && x!=5 && x!=9 && vis[x-1])
			dfs(x-1);
		if(x!=4 && x!=8 && x!=12 && vis[x+1])
			dfs(x+1);
		if(x!=1 && x!=2 && x!=3 && x!=4 && vis[x-4])
			dfs(x-4);
		if(x!=9 && x!=10 && x!=11 && x!=12 && vis[x+4])
			dfs(x+4);
	}

}
```

## **第八题：取球博弈**

两个人玩取球的游戏。
一共有N个球，每人轮流取球，每次可取集合{n1,n2,n3}中的任何一个数目。
如果无法继续取球，则游戏结束。
此时，持有奇数个球的一方获胜。
如果两人都是奇数，则为平局。

假设双方都采用最聪明的取法，
第一个取球的人一定能赢吗？
试编程解决这个问题。

输入格式：
第一行3个正整数n1 n2 n3，空格分开，表示每次可取的数目 (0<n1,n2,n3<100)
第二行5个正整数x1 x2 ... x5，空格分开，表示5局的初始球数(0<xi<1000)

输出格式：
一行5个字符，空格分开。分别表示每局先取球的人能否获胜。
能获胜则输出+，
次之，如有办法逼平对手，输出0，
无论如何都会输，则输出-

例如，输入：
1 2 3
1 2 3 4 5

程序应该输出：
+ 0 + 0 -

再例如，输入：
1 4 5
10 11 12 13 15

程序应该输出：
0 - 0 + +

再例如，输入：
2 3 5
7 8 9 10 11

程序应该输出：
+ 0 0 0 0

资源约定：
峰值内存消耗（含虚拟机） < 256M
CPU消耗  < 3000ms

请严格按要求输出，不要画蛇添足地打印类似：“请您输入...” 的多余内容。

所有代码放在同一个源文件中，调试通过后，拷贝提交该源码。
注意：不要使用package语句。不要使用jdk1.7及以上版本的特性。
注意：主类的名字必须是：Main，否则按无效代码处理

```
import java.util.Arrays;
import java.util.Scanner;

public class Main {

  private static int[] n;

  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    n = new int[3];
    for (int i = 0; i < 3; i++) {
      n[i] = sc.nextInt();
    }
    Arrays.sort(n);//排序
    for (int i = 0; i < 5; i++) {
      int num = sc.nextInt();
      char res = f(num, 0, 0);
      System.out.print(res + " ");
    }
    System.out.println();
  }
static char[][][]cache = new char[1000][2][2];
  /**
   * 参数代表着当前取球人面临的局面
   * @param num 球的总数
   * @param me 我方持有的数目-->我方数目的奇偶性
   * @param you 对手持有的数目-对方数目的奇偶性
   * @return
   */
  private static char f(int num, int me, int you) {
    if (num<n[0])//不够取
    {
      if ((me&1)==1&&(you&1)==0)return '+';
      else if ((me&1)==0&&(you&1)==1)return '-';
      else return '0';
    }
    if (cache[num][me][you]!='\0')return cache[num][me][you];
    boolean ping = false;
    for (int i = 0; i < 3; i++) {
      if (num >= n[i]) {
        char res = f(num - n[i], you, (n[i]&1)==0?me:(1-me));//注意此处，传递me和you的奇偶性
        if (res == '-')
        {
          cache[num][me][you]='+';
          return '+';
        }
        if (res == '0')
          ping = true;
      }
    }
    //如果能走到第这行，说明不存在对手输的情况，那么是否存在平的情况
    if (ping)
    {
      cache[num][me][you]='0';
      return '0';
    }
    else
    {
      cache[num][me][you]='-';
      return '-';
    }
  }
}
```

## **第九题：交换瓶子**

有N个瓶子，编号 1 ~ N，放在架子上。

比如有5个瓶子：
2 1 3 5 4

要求每次拿起2个瓶子，交换它们的位置。
经过若干次后，使得瓶子的序号为：
1 2 3 4 5

对于这么简单的情况，显然，至少需要交换2次就可以复位。

如果瓶子更多呢？你可以通过编程来解决。

输入格式为两行：
第一行: 一个正整数N（N<10000）, 表示瓶子的数目
第二行：N个正整数，用空格分开，表示瓶子目前的排列情况。

输出数据为一行一个正整数，表示至少交换多少次，才能完成排序。

例如，输入：
5
3 1 2 5 4

程序应该输出：
3

再例如，输入：
5
5 4 3 2 1

程序应该输出：
2

资源约定：
峰值内存消耗（含虚拟机） < 256M
CPU消耗  < 1000ms

请严格按要求输出，不要画蛇添足地打印类似：“请您输入...” 的多余内容。

所有代码放在同一个源文件中，调试通过后，拷贝提交该源码。
注意：不要使用package语句。不要使用jdk1.7及以上版本的特性。
注意：主类的名字必须是：Main，否则按无效代码处理

```
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		int n = in.nextInt();
		int[] a = new int[n+1];
		for(int i=1;i<=n;i++)
			a[i] = in.nextInt();
		int ans = 0;
		for(int i=1;i<=n;i++)
			if(a[i]!=i) 
				for(int j=i+1;j<=n;j++) {
					if(a[j]==i) {
						a[j]=a[i];
						a[i]=a[i];
						ans++;
						break;
					}
				}

		System.out.println(ans);

	}

}
```

## **第十题：压缩变换**

小明最近在研究压缩算法。
他知道，压缩的时候如果能够使得数值很小，就能通过熵编码得到较高的压缩比。
然而，要使数值很小是一个挑战。

最近，小明需要压缩一些正整数的序列，这些序列的特点是，后面出现的数字很大可能是刚出现过不久的数字。对于这种特殊的序列，小明准备对序列做一个变换来减小数字的值。

变换的过程如下：
从左到右枚举序列，每枚举到一个数字，如果这个数字没有出现过，刚将数字变换成它的相反数，如果数字出现过，则看它在原序列中最后的一次出现后面（且在当前数前面）出现了几种数字，用这个种类数替换原来的数字。

比如，序列(a1, a2, a3, a4, a5)=(1, 2, 2, 1, 2)在变换过程为：
a1: 1未出现过，所以a1变为-1；
a2: 2未出现过，所以a2变为-2；
a3: 2出现过，最后一次为原序列的a2，在a2后、a3前有0种数字，所以a3变为0；
a4: 1出现过，最后一次为原序列的a1，在a1后、a4前有1种数字，所以a4变为1；
a5: 2出现过，最后一次为原序列的a3，在a3后、a5前有1种数字，所以a5变为1。
现在，给出原序列，请问，按这种变换规则变换后的序列是什么。

输入格式：
输入第一行包含一个整数n，表示序列的长度。
第二行包含n个正整数，表示输入序列。

输出格式：
输出一行，包含n个数，表示变换后的序列。

例如，输入：
5
1 2 2 1 2

程序应该输出：
-1 -2 0 1 1

再例如，输入：
12
1 1 2 3 2 3 1 2 2 2 3 1

程序应该输出：
-1 0 -2 -3 1 1 2 2 0 0 2 2

数据规模与约定
对于30%的数据，n<=1000；
对于50%的数据，n<=30000；
对于100%的数据，1 <=n<=100000，1<=ai<=10^9

资源约定：
峰值内存消耗（含虚拟机） < 256M
CPU消耗  < 3000ms

请严格按要求输出，不要画蛇添足地打印类似：“请您输入...” 的多余内容。

所有代码放在同一个源文件中，调试通过后，拷贝提交该源码。
注意：不要使用package语句。不要使用jdk1.7及以上版本的特性。
注意：主类的名字必须是：Main，否则按无效代码处理

```
import java.util.HashSet;
import java.util.Scanner;

public class Main {

	static HashSet<Integer> set = new HashSet<>();

	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
		int n = in.nextInt();
		int[] a = new int[n+1];
		int[] b = new int[n+1];
		int[] pre = new int[n+1];

		for(int i=1;i<=n;i++) {
			a[i] = in.nextInt();
			int j=i-1;
			while(j>0 && a[j]!=a[i])
				j--;
			pre[i] = j;
		}

		for(int i=1;i<=n;i++) {
			if(pre[i]==0) 
				b[i] = -a[i];
			else {
				set.clear();
				for(int j=pre[i]+1;j<i;j++) 
					set.add(a[j]);
				b[i] = set.size();
			}
		}
		for(int i=1;i<=n;i++)
			if(i!=n)
				System.out.print(b[i]+" ");
			else
				System.out.println(b[i]);

	}

}
```