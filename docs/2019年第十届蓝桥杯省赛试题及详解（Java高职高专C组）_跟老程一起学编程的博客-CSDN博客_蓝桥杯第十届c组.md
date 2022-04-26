<!--yml
category: 蓝桥杯
date: 2022-04-26 11:07:18
-->

# 2019年第十届蓝桥杯省赛试题及详解（Java高职高专C组）_跟老程一起学编程的博客-CSDN博客_蓝桥杯第十届c组

> 来源：[https://blog.csdn.net/future277809183/article/details/123283093](https://blog.csdn.net/future277809183/article/details/123283093)

[【蓝桥杯】历年真题题目及题解汇总](https://blog.csdn.net/future277809183/article/details/122826573 "【蓝桥杯】历年真题题目及题解汇总")

* * *

1.  结果填空 (满分5分)
2.  结果填空 (满分5分)
3.  结果填空 (满分10分)
4.  结果填空 (满分10分)
5.  结果填空 (满分15分)
6.  程序设计（满分15分）
7.  程序设计（满分20分）
8.  程序设计（满分20分）
9.  程序设计（满分20分）
10.  程序设计（满分25分）
11.  程序设计（满分25分）

* * *

## **第一题：求和**

【问题描述】
小明对数位中含有 2、0、1、9 的数字很感兴趣，在 1 到 40 中这样的数包 括 1、2、9、10 至 32、39 和 40，共 28 个，他们的和是 574。 请问，在 1 到 2019 中，所有这样的数的和是多少？

**答案：1905111**

```
public class Main {        //1905111
    public static void main(String[] args) {
        int count=0,temp=0;
        for (int i = 1; i <=2019; i++) {
            int b = i;
            temp=i;
            while(b!=0){
                int a = b%10;
                if(a==2 || a==0||a==1||a==9){
                   count+=temp;
                    break;
                }
                b/=10;
            }
        }
        System.out.println(count);
    }
}
```

## **第二题：矩形切割**

【问题描述】
小明有一些矩形的材料，他要从这些矩形材料中切割出一些正方形。
当他面对一块矩形材料时，他总是从中间切割一刀，切出一块最大的正方 形，剩下一块矩形，然后再切割剩下的矩形材料，直到全部切为正方形为止。 例如，对于一块两边分别为 5 和 3 的材料（记为 5×3），小明会依次切出 3×3、2×2、1×1、1×1 共 4 个正方形。 现在小明有一块矩形的材料，两边长分别是 2019 和 324。请问小明最终会 切出多少个正方形？

```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int max = sc.nextInt();
        int min=sc.nextInt();
        int count=0,num,temp;
        while (true){
            if ( min==0){//当没有得时候就可以退出了
                break;
            }
             num =  max/min;//看看当前长宽不变得时候有几个正方形
             count+=num;    //把这些都加进来
             //替换一下，剪完正方形，之后，原来得长就变成了宽，原来的宽就成了长
            temp=max-min*num;//原来得长减去剪掉得几个宽，就是现在得宽
            max=min;
            min=temp;

        }
        System.out.println(count);
    }
} 
```

## **第三题：不同子串**

问题描述】
一个字符串的非空子串是指字符串中长度至少为 1 的连续的一段字符组成 的串。例如，字符串aaab 有非空子串a, b, aa, ab, aaa, aab, aaab，一共 7 个。 注意在计算时，只算本质不同的串的个数。 请问，字符串0100110001010001 有多少个不同的非空子串？

```
import java.util.HashSet;
import java.util.Set;

public class Main {//100
	public static void main(String[] args) {
		String s ="0100110001010001";
		Set<String> set = new HashSet<String>();       //Set最大的特点就是不能存重复的元素
		for (int i = 0; i < s.length(); i++) {        //for循环每一种可能，加入set里面
			for (int j = i+1; j <= s.length(); j++) {
				String a = s.substring(i,j);
				set.add(a);
			}
		}
		System.out.println(set.size());           
	}

}
```

## **第四题：质数**

【问题描述】
我们知道第一个质数是 2、第二个质数是 3、第三个质数是 5……请你计算 第 2019 个质数是多少？

```
public class Main {
	public static void main(String[] args) {
		int zs = 0;//声明一个标记用于存储求得质数的位数
		int a =1;  //声明一个用来循环的变量初始值
		while(zs<2019){//while 循环条件为位数到达2019停止;
			a++;//递增变量
			int i;
			for (i = 2; i <a; i++) {//循环2-a之间的数
				if(a%i==0){//判断有没有数能被a整除如果有跳出循环
					break;
				}
			}
			if(i==a){//如果上一步没有跳出循环则i等于a
				zs++;//位数增加
			}
		}
		System.out.println("第 2019 个质数是:"+a);
	}
} 
```

## **第五题：最大降雨量**

【问题描述】
由于沙之国长年干旱，法师小明准备施展自己的一个神秘法术来求雨。 这个法术需要用到他手中的 49 张法术符，上面分别写着 1 至 49 这 49 个 数字。法术一共持续 7 周，每天小明都要使用一张法术符，法术符不能重复使 用。 每周，小明施展法术产生的能量为这周 7 张法术符上数字的中位数。法术 施展完 7 周后，求雨将获得成功，降雨量为 7 周能量的中位数。 由于干旱太久，小明希望这次求雨的降雨量尽可能大，请大最大值是多少？

**答案：**
求的不是七周中位数的和，而是七周中位数的中位数的最大值

![](img/996d28e364def1598346e9328847a47f.png)

a,b,c,x,e,f,g分别是每周的中位数。

而x是a,b,c,x,e,f,g是这七周的每一周的中位数的中位数

题目的要求是让我们最大化这个x;

我们可以假定x已经是我们要求的值，那么为了让x符合题目信息，我们必须让第4周的后3天，第5，6，7周的后4天都大于这个值。

那么很显然有15个数比x大，那么x就等于49 - 15 = 34;

## **第六题：旋转**

【问题描述】
图片旋转是对图片最简单的处理方式之一，在本题中，你需要对图片顺时 针旋转 90 度。 我们用一个 n×m 的二维数组来表示一个图片，例如下面给出一个 3×4 的 图片的例子：
1 3 5 7 9 8 7 6 3 5 9 7
这个图片顺时针旋转 90 度后的图片如下：
3 9 1 5 8 3 9 7 5 7 6 7
给定初始图片，请计算旋转后的图片。
【输入格式】
输入的第一行包含两个整数 n 和 m，分别表示行数和列数。 接下来 n 行，每行 m 个整数，表示给定的图片。图片中的每个元素（像 素）为一个值为 0 至 255 之间的整数（包含 0 和 255）。
【输出格式】
输出 m 行 n 列，表示旋转后的图片。

【样例输入】 3 4 1 3 5 7 9 8 7 6 3 5 9 7
【样例输出】 3 9 1 5 8 3 9 7 5 7 6 7
【评测用例规模与约定】 对于 30% 的评测用例，1≤n,m≤10。 对于 60% 的评测用例，1≤n,m≤30。 对于所有评测用例，1≤n,m≤100

```
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		int [][] num = new int [n+1][m+1];
		for (int i = 1; i <=n; i++) {
			for (int j = 1; j <=m; j++) {
				num[i][j]=sc.nextInt();
			}
		}
		int [][]shu = new int [m+1][n+1];
		for (int i = 1; i <=m; i++) {
			for (int j = 1; j <=n; j++) {
				shu[i][j]=num[n-j+1][i];      
			}
		}
		for (int i = 1; i <=m; i++) {
			for (int j = 1; j <=n; j++) {
				System.out.print(shu[i][j]+" ");
			}
			System.out.println();
		}
	}

} 
```

## **第七题：外卖店优先级**

问题描述】
“饱了么”外卖系统中维护着 N 家外卖店，编号 1 ∼ N。每家外卖店都有 一个优先级，初始时 (0 时刻) 优先级都为 0。 每经过 1 个时间单位，如果外卖店没有订单，则优先级会减少 1，最低减 到 0；而如果外卖店有订单，则优先级不减反加，每有一单优先级加 2。 如果某家外卖店某时刻优先级大于 5，则会被系统加入优先缓存中；如果 优先级小于等于 3，则会被清除出优先缓存。 给定 T 时刻以内的 M 条订单信息，请你计算 T 时刻时有多少外卖店在优 先缓存中。
【输入格式】 第一行包含 3 个整数 N、M 和 T。 以下 M 行每行包含两个整数 ts 和 id，表示 ts 时刻编号 id 的外卖店收到 一个订单。
【输出格式】
输出一个整数代表答案。
【样例输入】 2 6 6 1 1 5 2 3 1 6 2 2 1 6 2
【样例输出】 1
【样例解释】 6 时刻时，1 号店优先级降到 3，被移除出优先缓存；2 号店优先级升到 6， 加入优先缓存。所以是有 1 家店 (2 号) 在优先缓存中。
【评测用例规模与约定】 对于 80% 的评测用例，1≤ N,M,T ≤10000。 对于所有评测用例，1≤ N,M,T ≤100000，1≤ts≤T，1≤id ≤ N。

```
import java.util.ArrayList;
import java.util.Map;
import java.util.Map.Entry;
import java.util.Scanner;
import java.util.TreeMap;

public class Main {
	static Scanner in = new Scanner(System.in);
	static int n, m, t;
	static Map<Integer, ArrayList<Integer>> map = new TreeMap<Integer, ArrayList<Integer>>();
	static int result;

	public static void main(String[] args) {
		n = in.nextInt();
		m = in.nextInt();
		t = in.nextInt();
		for (int i = 1; i <= m; ++i) {
			int time = in.nextInt();
			int id = in.nextInt();
			if (map.containsKey(id)) {
				map.get(id).add(time);
			} else {
				ArrayList<Integer> temp = new ArrayList<Integer>();
				temp.add(time);
				map.put(id, temp);
			}
		}

		ArrayList<Map.Entry<Integer, ArrayList<Integer>>> list = new ArrayList<Map.Entry<Integer, ArrayList<Integer>>>(
				map.entrySet());
		for (int i = 0; i < list.size(); ++i) {
			Entry<Integer, ArrayList<Integer>> entry = list.get(i);
			ArrayList<Integer> list2 = entry.getValue();
			int num = 0;
			int[] count = new int[t + 2];
			boolean flag = false;
			for (int j = 0; j < list2.size(); ++j)
				count[list2.get(j)]++;

			for (int j = 1; j <= t; ++j) {
				if (count[j] == 0) {
					if (num > 0)
						num--;
					if (num <= 3)
						flag = false;
				} else {
					num += count[j] * 2;
					if (num > 5)
						flag = true;
				}
			}
			if (flag)
				result++;
		}
		System.out.println(result);
	}

}
```

## **第八题： 人物相关性分析**

【问题描述】
小明正在分析一本小说中的人物相关性。他想知道在小说中 Alice 和 Bob 有多少次同时出现。 更准确的说，小明定义 Alice 和 Bob“同时出现”的意思是：在小说文本 中 Alice 和 Bob 之间不超过 K 个字符。 例如以下文本： ThisisastoryaboutAliceandBob.AlicewantstosendaprivatemessagetoBob. 假设 K = 20，则 Alice 和 Bob 同时出现了 2 次，分别是”Alice and Bob” 和”Bob. Alice”。前者 Alice 和 Bob 之间有 5 个字符，后者有 2 个字符。 注意: 1\. Alice 和 Bob 是大小写敏感的，alice 或 bob 等并不计算在内。 2\. Alice 和 Bob 应为单独的单词，前后可以有标点符号和空格，但是不能 有字母。例如 Bobbi 並不算出现了 Bob。
【输入格式】
第一行包含一个整数 K。 第二行包含一行字符串，只包含大小写字母、标点符号和空格。长度不超 过 1000000。
【输出格式】
输出一个整数，表示 Alice 和 Bob 同时出现的次数。
【样例输入】
20 This is a story about Alice and Bob.Alice wants to send aprivate message to Bob.

```
import java.util.Scanner;

public class Main {
	  public static void main(String[] args)  {
	        Scanner reader=new Scanner(System.in);
	        int res=0;    //save result
	        int K=reader.nextInt();
	        reader.nextLine();    //nextLine吸取回车键
	        String str=reader.nextLine();
	        String words[]=str.split("\\s+|\\.");    //以空格和.分割出来，注意.空格的组合存放为空字符串

	        //    Alice------>Bob
	        for(int i=0;i<words.length;i++){
	            if(words[i].equals("Alice")){
	                for(int j=i+1;j<words.length;j++){
	                    if(words[j].equals("Bob")){
	                        int sum=1;    //这里要等于1
	                        for(int k=i+1;k<j;k++){
	                            sum+=words[k].length()+1;
	                        }
	                        if(sum<=K){
	                            res++;
	                        }
	                    }
	                }
	            }
	        }

	        //Bob--------->Alice
	        for(int i=0;i<words.length;i++){
	            if(words[i].equals("Bob")){
	                for(int j=i+1;j<words.length;j++){
	                    if(words[j].equals("Alice")){
	                        int sum=1;    //这里要等于1
	                        for(int k=i+1;k<j;k++){
	                            sum+=words[k].length()+1;
	                        }
	                        if(sum<=K){
	                            res++;
	                        }
	                    }
	                }
	            }
	        }
	        System.out.println(res);
	    }

}
```

## **第九题：等差数列**

时间限制: 1.0s 内存限制: 512.0MB 本题总分：25 分
【问题描述】
数学老师给小明出了一道等差数列求和的题目。但是粗心的小明忘记了一 部分的数列，只记得其中 N 个整数。 现在给出这 N 个整数，小明想知道包含这 N 个整数的最短的等差数列有 几项？
【输入格式】
输入的第一行包含一个整数 N。 第二行包含 N 个整数 A1,A2,··· ,AN。(注意 A1 ∼ AN 并不一定是按等差数 列中的顺序给出)
【输出格式】
输出一个整数表示答案。
【样例输入】 5 2 6 4 10 20
【样例输出】 10
【样例说明】
包含 2、6、4、10、20 的最短的等差数列是 2、4、6、8、10、12、14、16、 18、20。
【评测用例规模与约定】
对于所有评测用例，2≤ N ≤100000，0≤ Ai ≤109。

```
import java.util.Arrays;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc =new Scanner(System.in);
        int n = sc.nextInt();
        int [] num = new int [n];			//输入的数
        int [] cha = new int [n-1];			//数组排序后，相邻的数字最小的差值
        for (int i = 0; i < num.length; i++) {
            num[i]=sc.nextInt();
        }
        Arrays.sort(num);
        int min_cha=Integer.MAX_VALUE;
        for (int i=0;i<cha.length;i++){
            cha[i]=num[i+1]-num[i];
            min_cha=Math.min(cha[i],min_cha);
        }
//        for (int i:cha
//             ) {
//            System.out.println(i);
//        }
        int dengcha=Integer.MAX_VALUE;
       A: for (;min_cha>0;min_cha--){
            boolean bool = false;
            for (int i=0;i<cha.length;i++){
                if (cha[i]%min_cha!=0){
                    continue A;
                }
            }
            dengcha=min_cha;
            break A;
        }
//        System.out.println(dengcha);
        int num1 = num[num.length-1]-num[0];
        int count=1;
        count+=num1/dengcha;
        System.out.println(count);
    }
}
```

## **第十题：扫地机器人**

【问题描述】
小明公司的办公区有一条长长的走廊，由 N 个方格区域组成，如下图所
示。
走廊内部署了 K 台扫地机器人，其中第 i 台在第 Ai 个方格区域中。 已知扫地机器人每分钟可以移动到左右相邻的方格中，并将该区域清扫干
净。
请你编写一个程序，计算每台机器人的清扫路线，使得

它们最终都返回出发方格，
每个方格区域都至少被清扫一遍，
从机器人开始行动到最后一台机器人归位花费的时间最少。
注意多台机器人可以同时清扫同一方块区域，它们不会互相影响。
输出最少花费的时间。 在上图所示的例子中，最少花费时间是 6。第一台路线：2-1-2-3-4-3-2，清 扫了 1、2、3、4 号区域。第二台路线 5-6-7-6-5，清扫了 5、6、7。第三台路线 10-9-8-9-10，清扫了 8、9 和 10。
【输入格式】
第一行包含两个整数 N 和 K。 接下来 K 行，每行一个整数 Ai。

【输出格式】
输出一个整数表示答案。
【样例输入】 10 3 5 2 10
【样例输出】 6
【评测用例规模与约定】
对于 30% 的评测用例，1≤ K < N ≤10。 对于 60% 的评测用例，1≤ K < N ≤1000。 对于所有评测用例，1≤ K < N ≤100000，1≤ Ai ≤ N

```
import java.util.Scanner;

public class Main {
	static int N;
	static int K;
	static int[] a = new int[1000000];
	static int[] b = new int[1000000];

	public static void main(String[] args) {
		int i,L;
		Scanner sc =new Scanner(System.in);
		N=sc.nextInt();
		K=sc.nextInt();
		for (  i = 1; i <=K; i++) {
			a[i]=sc.nextInt();
			b[a[i]]=1;
		}
		L=fun();
		System.out.println(2*(L-1));

	}

public static	boolean check1(int first_L, int L) { //第一个区间长度为 first_L，之后区间长度都为 L
		int i, j;
		if (first_L + (K - 1) * L < N) {//第一个区间再加上，其他的机器人和*这段的长度是不是能够够到总长
			return false;
		}
		i = 1; //第 i 个区间
		j = 1; //当前查看的方格位置
		while (j <= N) {
			if (b[j] == 1) { //第 i 个区间内有机器人
				j = first_L + (i - 1) * L + 1; //j 指向下一个区间起点
				i++; //下一个区间
			}
			else {
				j++;//一直检查下一个方格，如果一直没有直到first_L和j相等后，表明真的没有机器人
				if (j == first_L + (i - 1) * L + 1 || j == N + 1) { //第 i 个区间内没有机器人
					return false;		//因为L是不断变大的，first也一直变大，所以检查一直再往后扩展
				}
			}
		}
		return true;
	}
public static		boolean check(int L) {
		int first_L; //首区间的长度(取值范围：1~L)
		for (first_L = L; first_L > 0; first_L--) {//倒叙是因为，用大区间可以减少机器人的移动
			if (check1(first_L, L)) {
				return true;
			}
		}
		return false;
	}
public static		int fun() {
		int i, j, L;
		for (L = N / K; L <= N; L++) {//平均一下，
			if (check(L)) {
				return L;
			}
		}
		return L;
	}

}
```