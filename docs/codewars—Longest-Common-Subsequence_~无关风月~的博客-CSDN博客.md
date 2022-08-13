<!--yml
category: codewars
date: 2022-08-13 11:42:37
-->

# codewars—Longest Common Subsequence_~无关风月~的博客-CSDN博客

> 来源：[https://blog.csdn.net/zxm1306192988/article/details/72835759?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-19-72835759-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/zxm1306192988/article/details/72835759?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-19-72835759-null-null.142^v40^control,185^v2^control&utm_term=codewars)

题目地址：[https://www.codewars.com/kata/longest-common-subsequence/train/java](https://www.codewars.com/kata/longest-common-subsequence/train/java)

### 求两个字符串的最大公共序列

最长公共子串（Longest CommonSubstring）和最长公共子序列（LongestCommon Subsequence, LCS）的区别：子串（Substring）是串的一个连续的部分，子序列（Subsequence）则是从不改变序列的顺序，而从序列中去掉任意的元素而获得的新序列；更简略地说，前者（子串）的字符的位置必须连续，后者（子序列LCS）则不必。

```
 @Test
    public void exampleTests() {
        long startTime=System.nanoTime()
        assertEquals("", Solution.lcs("a", "b"))
        assertEquals("abc", Solution.lcs("abcdef", "abc"))
        assertEquals("acf", Solution.lcs("abcdef", "acf"))
        assertEquals("12356", Solution.lcs("132535365", "123456789"))
//        assertEquals("BCBA", Solution.lcs("ABCBDAB", "BDCABA"))
        long endTime=System.nanoTime()
        System.out.println("程序运行时间： "+(endTime-startTime)+"ns")
    }
```

方法一：
Brute-Force算法（暴力枚举）：
X和Y的所有子序列都检查过后即可求出X和Y的最长公共子序列。X的一个子序列相应于下标序列{1, 2, …, m}的一个子序列，因此，X共有2m个不同子序列（Y亦如此，如为2^n），从而穷举搜索法需要指数时间（2^m * 2^n）。

```
class Solution {
    public static String lcs(String x, String y) {
        if(x.length()<y.length()){
            String z=x;
            x=y;
            y=z;
        }
        String maxstr="";
        for(int i=0;i<y.length();i++){
            StringBuilder strB=new StringBuilder();
            int a=x.indexOf(y.charAt(i));
            if(a==-1){
                continue;
            }else{
                strB.append(y.charAt(i));
                x=x.substring(a);
                for(int j=i+1;j<y.length();j++){
                    a=x.indexOf(y.charAt(j));
                    if(a==-1){
                        continue;
                    }else{
                        strB.append(y.charAt(j));
                        x=x.substring(a);
                    }
                }
            }
            if(strB.length()>maxstr.length()){
                maxstr=strB.toString();
            }
        }

        return maxstr;
    }
}
```

方法二：
LCS 最大公共序列算法
聪明的程序员想到了，一个用矩阵来查找的算法，就是把两个队列用整形矩阵表示， 相同的为1， 不同的为0， 然后求最大对角线，优化是优化了很多， 不过求最大对角线也不省心。

聪明的程序员再次优化了算法，就是相同的不是用1表示， 而是数字叠加，只需求最后一行前后数字查为1的列的对应字母（也可求最大对角线），时间复杂度也降到了 O（mn）+O(m+n)
比如求 x = “acf” and y = “abcdef”

```
 a  b  c  d  e  f
  [0, 0, 0, 0, 0, 0, 0]

a [0, 1, 1, 1, 1, 1, 1]

c [0, 1, 1, 2, 2, 2, 2]

f [0, 1, 1, 2, 2, 2, 3]
```

```
 class Solution {
    public static String lcs(String x, String y) {

                int m = x.length(), n = y.length();
        int[][] nums = new int[m + 1][n + 1];
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                nums[i][j] = nums[i - 1][j - 1] + (x.charAt(i - 1) == y.charAt(j - 1) ? 1 : 0);
                nums[i][j] = Math.max(nums[i][j], nums[i - 1][j]);
                nums[i][j] = Math.max(nums[i][j], nums[i][j - 1]);
            }
        }
        StringBuilder sb = new StringBuilder();
        for(int i = 1; i <= n; i++) {
            if (nums[m][i] - nums[m][i - 1] == 1) {
                sb.append(y.charAt(i - 1));
            }
        }
        return sb.toString();
    }
}
```

方法三：
动态规划算法
递归

记：
Xi=﹤x1，⋯，xi﹥ 即X序列的前 i 个字符 (1≤i≤m)（前缀）
Yj=﹤y1，⋯，yj﹥ 即Y序列的前 j 个字符 (1≤j≤n)（前缀）
假定
Z=﹤z1，⋯，zk﹥∈ LCS(X , Y)

*   若xm=yn（最后一个字符相同），则不难用反证法证明：该字符必是X与Y的任一最长公共子序列Z（设长度为k）的最后一个字符，即有zk = xm = yn 且显然有Zk-1∈LCS(Xm-1 , Yn-1)即Z的前缀Zk-1是Xm-1与Yn-1的最长公共子序列。此时，问题化归成求Xm-1与Yn-1的LCS（LCS(X , Y)的长度等于LCS(Xm-1 , Yn-1)的长度加1）。
*   若xm≠yn，则亦不难用反证法证明：要么Z∈LCS(Xm-1, Y)，要么Z∈LCS(X , Yn-1)。由于zk≠xm与zk≠yn其中至少有一个必成立，若zk≠xm则有Z∈LCS(Xm-1 , Y)，类似的，若zk≠yn 则有Z∈LCS(X , Yn-1)。此时，问题化归成求Xm-1与Y的LCS及X与Yn-1的LCS。LCS(X , Y)的长度为：max{LCS(Xm-1 , Y)的长度, LCS(X , Yn-1)的长度}。

另外两个序列的LCS中包含了两个序列的前缀的LCS，故问题具有最优子结构性质考虑用动态规划法。

最长公共子序列的结构有如下表示：

设序列X=< x1, x2, …, xm > 和 Y=< y1, y2, …, yn > 的一个最长公共子序列 Z=< z1, z2, …, zk >，则：

1.  若xm=yn，则zk=xm=yn且Zk-1是Xm-1和Yn-1的最长公共子序列；
2.  若xm≠yn且zk≠xm ，则Z是Xm-1和Y的最长公共子序列；
3.  若xm≠yn且zk≠yn ，则Z是X和Yn-1的最长公共子序列。

其中Xm-1=< x1, x2, …, xm-1 >，Yn-1=< y1, y2, …, yn-1 >，Zk-1=< z1, z2, …, zk-1 >。

但是这个发现费时很高~

```
public class Solution {
    public static String lcs(String x, String y) {
       if (x.length() == 0 || y.length() == 0)
          return ""

       String xlast=x.substring(x.length()-1)
       String ylast=y.substring(y.length()-1)
       if (xlast.equals(ylast))
         return lcs( x.substring(0,x.length()-1), y.substring(0,y.length()-1) ) + ylast

       String lcsA = lcs( x, y.substring(0,y.length()-1) )
       String lcsB = lcs( x.substring(0,x.length()-1), y )

       return (lcsA.length() > lcsB.length() ? lcsA : lcsB)
    }
}
```

### 最长递增子序列问题 Longest Increasing Subsequence (LIS)

设L=< a1,a2,…,an>是n个不同的实数的序列，L的递增子序列是这样一个子序列 Lin=< aK1,ak2,…,akm >，其中k1< k2 <…< km 且 aK1< ak2< …< akm。求这个子序列。

#### 第一种算法：转化为LCS问题求解

设序列 X=< b1,b2,…,bn>是对序列 L=< a1,a2,…,an>按递增排好序的序列。那么显然X与L的最长公共子序列即为 L 的最长递增子序列。这样就把求最长递增子序列的问题转化为求最长公共子序列问题LCS了。

```
public class Main2 {
    public static void main(String[] args) {
        int[] x={2,3,7,1,4,9,1};
        List<Integer> listx=new ArrayList<Integer>();
        List<Integer> listy=new ArrayList<Integer>();
        for(int i=0;i<x.length;i++){
            listx.add(x[i]);
            listy.add(x[i]);
        }
        Collections.sort(listy);

        System.out.println(new Solution().LCS(listx,listy));
    }
}

class Solution {
    public static List<Integer> LCS(List x, List y) {
       List<Integer> resultlist=new ArrayList<Integer>();
       if (x.size() == 0 || y.size() == 0)
          return new ArrayList<Integer>();

       int xlast=(int) x.subList(x.size()-1,x.size()).get(0);
       int ylast=(int) y.subList(y.size()-1,y.size()).get(0);
       if (xlast==ylast){
          resultlist.addAll(LCS( x.subList(0,x.size()-1), y.subList(0,y.size()-1)) );
          resultlist.add(ylast);
          return resultlist;
       }

       List lcsA = LCS( x, y.subList(0,y.size()-1) );
       List lcsB = LCS( x.subList(0,x.size()-1), y );

       return (lcsA.size() > lcsB.size() ? lcsA : lcsB);
    }
}
```

#### 第二种算法：动态规划

确定状态：以第 i 项结尾的最长递增子序列的长度为 f(i)
初始状态：以a[0]结尾的最长递增子序列是他本身，所有长度为1，f(0)=1
终止状态：max{ f(0),f(1),f(2)…f(n-1) }
决策：已知全部 j < x的 f(j)。如果 a[j] < a[i] ,显然可以把 a[i] 连在 a[j] 的后面
无后效性：f(i) 只与当前正在判断的 a[j] 相关
收益表示： `f(i)=max{ f(j)| j<i 且 a[j]<a[i] } + 1`

时间复杂度：枚举i ,枚举 j 找到最大满足条件的 j ,所以为 O(n2) O ( n 2 )
空间复杂度：存储每个 f(i) ,所以为 O(n) O ( n )

```
 public static void lis(int[] a) {
        int n = a.length;
        int[] f = new int[n];
        f[0] = 1;
        int max = 0;

        for (int i = 1; i < n; i++)
        {
            f[i] = 1;
            for (int j = 0; j < i; j++)
            {
                if (a[j] < a[i] && f[j] >= f[i])
                    f[i] = f[j] + 1;
            }
            if (f[i] > max) {
                max = f[i];
            }
        }

        System.out.println(max);
    }
```

需要输入最长递增子序列：
如果有多个，只需出入一个

对于每个 f(i) 记录得到他的决策 j , 即能与该位置数字构成最长递增子序列的上一个数字的位置，用数组 prePosition[n] 保存
用变量 maxIndex 记录最大的 f[i] 的位置
最后依次从 prePosition[n] 中向前找，即可得到 最大递增子序列

```
 public static void lis(int[] a) {
        int n = a.length;
        int[] f = new int[n];
        int[] prePosition = new int[n];
        f[0] = 1;
        prePosition[0] = -1;
        int maxIndex=-1;

        int max = 0;

        for (int i = 1; i < n; i++)
        {
            f[i] = 1;
            prePosition[i] = -1;
            for (int j = 0; j < i; j++)
            {
                if (a[j] < a[i] && f[j] >= f[i]) {
                    f[i] = f[j] + 1;
                    prePosition[i] = j;
                }
            }
            if (f[i] > max) {
                max = f[i];
                maxIndex=i;
            }
        }

        int[] subSequence = new int[max];
        subSequence[max - 1] = a[maxIndex];
        int pre = prePosition[maxIndex];
        for (int j = max - 2; j >= 0; j--) {
            subSequence[j] = a[pre];
            pre = prePosition[pre];
        }

        for (int k = 0; k < max; k++) {
            System.out.print(subSequence[k]);
            if (k != max - 1) {
                System.out.print(" ");
            } else {
                System.out.println();
            }
        }
    }
```

另一种写法，以前面类似，用 `ArrayList<ArrayList<Integer>> res` 在循环中直接保存，以每个位置结尾的最大递增子序列，用变量 maxIndex 记录最大的 f[i] 的位置，最后 res.get(maxIndex) 即为所求。

```
class Solution {
    public static ArrayList<Integer> maxSubIncreaseArray(int[] a) {
        int n = a.length;
        int[] f = new int[n];
        ArrayList<ArrayList<Integer>> res = new ArrayList<ArrayList<Integer>>();
        ArrayList<Integer> tmp = new ArrayList<Integer>();
        int index = -1;

        int maxIndex = 0;
        int max = Integer.MIN_VALUE;

        f[0] = 1;
        tmp.add(a[0]);
        res.add(tmp);

        for (int i = 1; i < n; i++) {
            index = -1;
            tmp = new ArrayList<Integer>();
            f[i] = 1;
            for (int j = 0; j < i; j++) {
                if (a[j] < a[i] && f[j] >= f[i]) {
                    f[i] = f[j]+1;
                    index = j;
                }
            }
            if (f[i] > max) {
                max = f[i];
                maxIndex = i;
            }

            if (index > -1) {
                tmp.addAll(res.get(index));
            }

            tmp.add(a[i]);

            res.add(tmp);
        }

        return res.get(maxIndex);
    }
}
```