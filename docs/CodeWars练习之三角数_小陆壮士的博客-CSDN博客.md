<!--yml
category: codewars
date: 2022-08-13 11:43:24
-->

# CodeWars练习之三角数_小陆壮士的博客-CSDN博客

> 来源：[https://blog.csdn.net/qingyi2xiaosheng/article/details/52117018?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-52117018.nonecase](https://blog.csdn.net/qingyi2xiaosheng/article/details/52117018?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-52117018.nonecase)

今天遇到一个题目：判断一个数是不是三角数。三角数的意思是，从1到这个数以第n行n个数刚好能排出n行。就好像1，3，6，10是三角数一样。

```
 1
 2 3
4 5 6
```

我开始的想法是判断这个数是不是从1到某个数的和，在求和这里我用了递归，结果在数值比较大的时候出现了栈溢出的情况。像这样：

```
public static int sum(int n){
		 if(n==1||n==0){
			 return n;
		 }else{
			 return n*sum(n-1);
		 }
	}
```

因为栈溢出所以是不过关的程序嘛，然后就查了一下是否有三角数这个概念，果然有，而且第一个规则就是：如果N*(N+1)/2等于N，则N就是三角数。可是这个公式不正是等差数列求和公式吗，公差是1。然后我就修改了sum函数，如下：

```
public static int sum(int n){
		 return n*(n+1)/2;
	}
```

最终的解法是：

```
 public static boolean isTriangleNumber(long number) {
		boolean flag=false;
		int n=0;
		while(n<number){
			if (number==sum(n)) {
				flag=true;
				break;
			}
			n++;			
		}
		return flag;		
  }
```

写完之后本来想提交的，然后仔细看了一下很多人的解法，他们都是用这个法子：

```
public class TriangleNumbers {

  public static Boolean isTriangleNumber(long number) {
    /* if A is a triangle number with N level, then A = (N +1)*N/2
     * then, we have : N^2 + N -2A = 0
     * solve this equation and check if N is an integer
     * to conclude whether A is a triangle number or not.
     * Delta = 1 + 8A => N = [-1+ SQRT(Delta)]/2
     */
    double N = (Math.sqrt(1+number*8) - 1)/2;
    return (N == Math.round(N));
  }
}
```

再重新看资料，才发现确实有这个法子：

可是还是看不懂

![大哭](img/6a4af3e4e28259d05f74edb62c699bc6.png) ![大哭](img/6a4af3e4e28259d05f74edb62c699bc6.png)

，主要也是看到很多人都用这个法子，然后看到英文的时候还是会偶尔略过。然后问同学才想起来，这里就是求n的啊，一元二次方程的解。

所以这就是上面的解法了。哦耶！