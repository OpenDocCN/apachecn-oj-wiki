<!--yml
category: codewars
date: 2022-08-13 11:37:13
-->

# 【CodeWars】Square into Squares. Protect trees!_MyMyGeek的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_24342739/article/details/90544539?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-24-90544539-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_24342739/article/details/90544539?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-24-90544539-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## 1.题意

> 题目链接：[https://www.codewars.com/kata/54eb33e5bc1a25440d000891](https://www.codewars.com/kata/54eb33e5bc1a25440d000891)

```
My little sister came back home from school with the following task: given a squared sheet of paper she has to cut it in pieces which, when assembled, give squares the sides of which form an increasing sequence of numbers. At the beginning it was lot of fun but little by little we were tired of seeing the pile of torn paper. So we decided to write a program that could help us and protects trees.

Task
Given a positive integral number n, return a strictly increasing sequence (list/array/string depending on the language) of numbers, so that the sum of the squares is equal to n².

If there are multiple solutions (and there will be), return the result with the largest possible values:

Examples
decompose(11) must return [1,2,4,10]. Note that there are actually two ways to decompose 11², 11² = 121 = 1 + 4 + 16 + 100 = 1² + 2² + 4² + 10² but don't return [2,6,9], since 9 is smaller than 10.

For decompose(50) don't return [1, 1, 4, 9, 49] but [1, 3, 5, 8, 49] since [1, 1, 4, 9, 49] doesn't form a strictly increasing sequence.

Note
Neither [n] nor [1,1,1,…,1] are valid solutions. If no valid solution exists, return nil, null, Nothing, None (depending on the language) or "[]" (C) ,{} (C++), [] (Swift, Go).

The function "decompose" will take a positive integer n and return the decomposition of N = n² as:

[x1 ... xk] or
"x1 ... xk" or
Just [x1 ... xk] or
Some [x1 ... xk] or
{x1 ... xk} or
"[x1,x2, ... ,xk]"
depending on the language (see "Sample tests")

Note for Bash
decompose 50 returns "1,3,5,8,49"
decompose 4  returns "Nothing"
Hint
Very often xk will be n-1. 
```

这题的意思是给定一个数字n，在经过decompose(n)处理之后得到一个一组数字，这组数字的平方和要等于n^2，这组数中最大值要小于n(如果可以等于n的话直接返回n就是了)，并且如果存在多组解需要取最大值最大的那组解。就像题目中的例子说的那样：

## 2.代码

解法是通过递归来完成的，自定义了一个递归方法recurseDecompose。思路是把问题转换为一个数N是否是某些数的平方和，最开始这个N=n*n，递归求解转换过来的问题。

> 比如：当n=12时，N=n<sup>2</sup>=144，需要找一组数字x<sub>1</sub>,x<sub>2</sub>…x<sub>n</sub>满足N=x<sub>1</sub><sup>2</sup>+x<sub>2</sub><sup>2</sup>+…+x<sub>k</sub><sup>2</sup>，先从11作为这组数字中最大值开始找是否找到符合条件的一组数字，将11<sup>2</sup>从N中减去N’=N-11<sup>2</sup>，此时递归求解子问题，即N’是否某些数的平方和，依次类推，整个就是一个递归求解的过程。注意到递归方法里面有一个循环(注意循环变量一定要是递减的)，这是因为有可能11最为这组数最大值时无解，则需要继续找这组数字最大值是10、9、8…时是否有解，一旦找到一个解就返回，因为第一次找到的解，最大值才是最大的。

```
public class Decompose {
    public String decompose(long n) {
        String result = null;

        for (long i = n - 1; i > 1; i--) {
            long square = n * n;
            result = recurseDecompose(i, square);
            if (result != null) break;
        }

        return result;
    }

    public static String recurseDecompose(long i, long rem) {
        if (i * i == rem) {
            return i + "";
        } else if (i * i < rem) {
            rem = rem - i * i;

            for (long j = i - 1; j > 0; j--) {
                String tmp = recurseDecompose(j, rem);

                if (tmp != null) {
                    System.out.println(tmp + " " + i);
                    return tmp + " " + i;
                } else {
                    continue;
                }
            }
        } else {
            return null;
        }

        return null;
    }
} 
```

测试用例

```
import static org.junit.Assert.*;
import Decompose;
import org.junit.Test;

public class DecomposeTest {

    @Test
    public void test1() {
        Decompose d = new Decompose();
        long n = 11;
        assertEquals("1 2 4 10", d.decompose(n));
    }

    @Test
    public void test2() {
        Decompose d = new Decompose();
        long n = 12;
        assertEquals("1 2 3 7 9", d.decompose(n));
    }

    @Test
    public void test3() {
        Decompose d = new Decompose();
        long n = 50;
        assertEquals("1 3 5 8 49", d.decompose(n));
    }
} 
```