<!--yml
category: codewars
date: 2022-08-13 11:49:42
-->

# 【Codewars】Integers: Recreation One_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/90603793?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-90603793.nonecase](https://blog.csdn.net/ecysakura/article/details/90603793?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-90603793.nonecase)

### Codewars里的 5kyu Kata。

### 题目说明：

> Divisors of 42 are : 1, 2, 3, 6, 7, 14, 21, 42\. These divisors squared are: 1, 4, 9, 36, 49, 196, 441, 1764\. The sum of the squared divisors is 2500 which is 50 * 50, a square!
> 
> Given two integers m, n (1 <= m <= n) we want to find all integers between m and n whose sum of squared divisors is itself a square. 42 is such a number.
> 
> The result will be an array of arrays or of tuples (in C an array of Pair) or a string, each subarray having two elements, first the number whose squared divisors is a square and then the sum of the squared divisors.
> 
> #Examples:
> 
> ```
> list_squared(1, 250) --> [[1, 1], [42, 2500], [246, 84100]]
> list_squared(42, 250) --> [[42, 2500], [246, 84100]]
> ```
> 
> The form of the examples may change according to the language, see `Example Tests:` for more details.
> 
> **Note**
> 
> In Fortran - as in any other language - the returned string is not permitted to contain any redundant trailing whitespace: you can use dynamically allocated character strings.

### 解题代码：

```
import java.util.ArrayList;

public class SumSquaredDivisors {

    public static String listSquared(long m, long n) {
         // your code
        ArrayList<Long> divisors = new ArrayList<Long>();
        ArrayList<ArrayList<Long>> res = new ArrayList<ArrayList<Long>>();

        for (long c = m; c < n; c++) {
            divisors.clear();
            //divisors.add((long) 1);
            for (long i = 1; i <= c / 2; i++) {
                if (c % i == 0) {
                    divisors.add(i);
                }
            }
            divisors.add(c);

            long sum = new Long(0);
            for (int i = 0; i < divisors.size(); i++) {
                sum += (long) Math.pow(divisors.get(i).longValue(), 2);
            }

            Long s = new Long(sum);
            Double d = new Double(Math.sqrt(sum));

            if (d.toString().substring(d.toString().indexOf('.')).equals(".0")) {
                ArrayList r = new ArrayList<Long>();
                r.add(c);
                r.add(sum);
                res.add(r);
            }

        }

        return res.toString();
    }
}
```

Test Cases:

```
import static org.junit.Assert.*;

import java.util.Random;

import org.junit.Test;

public class SumSquaredDivisorsTest {

    private static long[] solAux(long n) {
        long s = 0;
        long nf = 0;
        long[] res = new long[2];
        for (long i = 1; i <= Math.floor(Math.sqrt(n)); i += 1) {
            if (n % i == 0) {
                s += i * i;
                nf = n / i;
                if (nf != i)
                    s += nf * nf;
            }
        }
        if (Math.pow((long) Math.sqrt(s), 2) == s) {
            res[0] = n;
            res[1] = s;
            return res;
        } else
            return null;
    }

    public static String solution(long m, long n) {
        String res = "[";
        for (long i = m; i <= n; i++) {
            long[] r = solAux(i);
            if (r != null) {
                res += "[" + Long.toString(r[0]) + ", " + Long.toString(r[1]) + "], ";
            }
        }
        return res.replaceFirst(",\\s$", "") + "]";
    }

    @Test
    public void test1() {
        assertEquals("[[1, 1], [42, 2500], [246, 84100]]", SumSquaredDivisors.listSquared(1, 250));
    }

    @Test
    public void test2() {
        assertEquals("[[42, 2500], [246, 84100]]", SumSquaredDivisors.listSquared(42, 250));
    }

    @Test
    public void test3() {
        assertEquals("[[287, 84100]]", SumSquaredDivisors.listSquared(250, 500));
    }

    @Test
    public void test4() {
        assertEquals("[]", SumSquaredDivisors.listSquared(300, 600));
    }

    @Test
    public void test5() {
        assertEquals("[[728, 722500], [1434, 2856100]]", SumSquaredDivisors.listSquared(600, 1500));
    }

    @Test
    public void test6() {
        assertEquals("[[1673, 2856100]]", SumSquaredDivisors.listSquared(1500, 1800));
    }

    @Test
    public void test7() {
        assertEquals("[[1880, 4884100]]", SumSquaredDivisors.listSquared(1800, 2000));
    }

    @Test
    public void test8() {
        assertEquals("[]", SumSquaredDivisors.listSquared(2000, 2200));
    }

    @Test
    public void test9() {
        assertEquals("[[4264, 24304900]]", SumSquaredDivisors.listSquared(2200, 5000));
    }

    @Test
    public void test10() {
        assertEquals("[[6237, 45024100], [9799, 96079204], [9855, 113635600]]",
                SumSquaredDivisors.listSquared(5000, 10000));
    }

    @Test
    public void testA() {
        System.out.println("****** Random test ******");
        Random rnd = new Random();
        for (int i = 0; i < 20; i++) {
            int m = Math.round(rnd.nextInt(25) * (42 - 2) + 200);
            int n = Math.round(rnd.nextInt(125) * (42 - 2) + 1100);
            System.out.println("listSquared m: " + m + " n: " + n);
            assertEquals(SumSquaredDivisorsTest.solution(m, n), SumSquaredDivisors.listSquared(m, n));
        }
    }

}
```

### 个人总结：

```
import java.util.stream.LongStream;

public class SumSquaredDivisors {

    public static String listSquared(long m, long n) {
        // your code
        String result = "[";
        for (long i = m; i <= n; i++) {
            if (Math.round(Math.sqrt(sumOfSquareDivisors(i))) == Math.sqrt(sumOfSquareDivisors(i))) {
                result += "[" + i + ", " + sumOfSquareDivisors(i) + "], ";
            }
        }
        return result.length() > 1 ? result.substring(0, result.length() - 2) + "]" : "[]";
    }

    public static long sumOfSquareDivisors(long n) {
        return LongStream.range(1, n + 1).filter(i -> n % i == 0).map(i -> i * i).sum();
    }
}
```

```
import java.util.ArrayList;
import java.util.List;

public class SumSquaredDivisors {

    public static String listSquared(long m, long n) {
        List<List<Integer>> finalRes = new ArrayList<List<Integer>>();
        for (long i = m; i <= n; i++) {
            double result = 0;
            for (int y = 1; y <= i; y++) {
                if (i % y == 0) {
                    result = result + Math.pow(y, 2);
                }
            }
            if (Math.sqrt(result) % 1 == 0) {
                List<Integer> pair = new ArrayList<Integer>();
                pair.add((int) i);
                pair.add((int) result);
                finalRes.add(pair);
            }
        }
        return finalRes.toString();
    }
}
```

```
import java.util.ArrayList;
import java.util.stream.LongStream;

public class SumSquaredDivisors {

    public static String listSquared(long m, long n) {
        ArrayList<String> strings = new ArrayList<>();
        LongStream.rangeClosed(m, n).forEach(current -> {
            long sum = LongStream.rangeClosed(1, current).filter(i -> current % i == 0).map(i -> i * i).sum();
            if (Math.sqrt(sum) % 1 == 0)
                strings.add(String.format("[%d, %d]", current, sum));
        });
        return String.valueOf(strings);
    }
}
```

```
import java.util.Arrays;
import java.util.stream.LongStream;

public class SumSquaredDivisors {

    public static String listSquared(long m, long n) {
        // your code
        String[] tempResult = LongStream.rangeClosed(m, n).boxed().map(l -> new long[] { l, sumSquaredDivisors(l) })
                .filter(ls -> isSquared(ls[1])).map(Arrays::toString).toArray(String[]::new);
        return Arrays.toString(tempResult);
    }

    private static boolean isSquared(long n) {
        long sqrtN = (long) Math.sqrt(n);
        return sqrtN * sqrtN == n;
    }

    private static long sumSquaredDivisors(long n) {
        return LongStream.rangeClosed(1, (long) Math.sqrt(n)).filter(l -> n % l == 0)
                .map(l -> (l * l) + ((n / l) == l ? 0 : (n / l) * (n / l))).sum();
    }
}
```