<!--yml
category: codewars
date: 2022-08-13 11:37:51
-->

# 【Codewars】Is a number prime?_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/90707211?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-9-90707211-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/ecysakura/article/details/90707211?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-9-90707211-null-null.142^v40^control,185^v2^control&utm_term=codewars)

### Codewars里的 6kyu Kata。

### 题目说明：

> Description:
> 
> Define a function that takes an integer argument and returns logical value `true` or `false` depending on if the integer is a prime.
> 
> Per Wikipedia, a prime number (or a prime) is a natural number greater than 1 that has no positive divisors other than 1 and itself.
> 
> ## Example
> 
> ```
> is_prime(1)  /* false */
> is_prime(2)  /* true  */
> is_prime(-1) /* false */
> ```
> 
> ## Assumptions
> 
> *   You can assume you will be given an integer input.
> *   You can not assume that the integer will be only positive. You may be given negative numbers as well (or `0`).
> *   There are no fancy optimizations required, but still *the* most trivial solutions might time out. Try to find a solution which does not loop all the way up to `n`.

### 解题代码：

```
public class Prime {
    public static boolean isPrime(int num) {
        //TODO
        if(num <= 1)return false;
        if(num == 2 || num == 3)return true;
        if(num % 6 != 5 && num % 6 != 1)return false;
        int div = 5;
        while(div <= (int)Math.sqrt(num)){
            if(num%(div) == 0 || num%(div+2) == 0)return false;
            div+=6;
        }
        return true;
    }
}
```

Test Cases:

```
import static org.junit.Assert.assertTrue;

import java.math.BigInteger;
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Random;

import static org.junit.Assert.assertFalse;
import org.junit.Test;

public class PrimeTest {

    @Test
    public void testBasic() {
        assertFalse("0  is not prime", Prime.isPrime(0));
        assertFalse("1  is not prime", Prime.isPrime(1));
        assertTrue("2  is prime", Prime.isPrime(2));
        assertTrue("73 is prime", Prime.isPrime(73));
        assertFalse("75 is not prime", Prime.isPrime(75));
        assertFalse("-1 is not prime", Prime.isPrime(-1));
    }

    @Test
    public void testPrime() {
        assertTrue("3 is prime", Prime.isPrime(3));
        assertTrue("5 is prime", Prime.isPrime(5));
        assertTrue("7 is prime", Prime.isPrime(7));
        assertTrue("41 is prime", Prime.isPrime(41));
        assertTrue("5099 is prime", Prime.isPrime(5099));
    }

    @Test
    public void testNotPrime() {
        assertFalse("4 is not prime", Prime.isPrime(4));
        assertFalse("6 is not prime", Prime.isPrime(6));
        assertFalse("8 is not prime", Prime.isPrime(8));
        assertFalse("9 is not prime", Prime.isPrime(9));
        assertFalse("45 is not prime", Prime.isPrime(45));
        assertFalse("-5 is not prime", Prime.isPrime(-1));
        assertFalse("-8 is not prime", Prime.isPrime(-1));
        assertFalse("-41 is not prime", Prime.isPrime(-1));
    }

    private static final Random rnd = new Random();
    private static final int MAX = 2_000_000_000;

    @Test
    public void testRandom() {

        List<TestCaseSpec> testCases = new ArrayList<>();

        try {

            // prime numbers
            for (int i = 0; i < 500; ++i) {
                int num = BigInteger.valueOf(rnd.nextInt(MAX)).nextProbablePrime().intValueExact();
                testCases.add(TestCaseSpec.make(num, true));
            }

            // composite numers (odd and even)
            for (int i = 0; i < 450; ++i) {
                int p1 = BigInteger.valueOf(rnd.nextInt(MAX)).nextProbablePrime().intValueExact();
                int p2 = BigInteger.valueOf(p1).nextProbablePrime().intValueExact();
                int num = rnd.nextInt(p2 - p1 - 1) + p1 + 1;
                testCases.add(TestCaseSpec.make(num, false));
            }

            // squares of a prime
            final int ms = (int) Math.sqrt(MAX) - 1000;
            for (int i = 0; i < 40; ++i) {
                int p1 = BigInteger.valueOf(rnd.nextInt(ms)).nextProbablePrime().intValueExact();
                int num = p1 * p1;
                testCases.add(TestCaseSpec.make(num, false));
            }

            // negative numbers
            for (int i = 0; i < 10; ++i) {
                int p1 = BigInteger.valueOf(rnd.nextInt(ms)).nextProbablePrime().intValueExact();
                int num = -p1;
                testCases.add(TestCaseSpec.make(num, false));
            }

        } catch (ArithmeticException ex) {
            throw new RuntimeException(
                    "Error occured when generating a test case. Please retry or raise the kata issue and paste the stack trace.",
                    ex);
        }

        Collections.shuffle(testCases);
        for (TestCaseSpec testCase : testCases) {

            boolean expected = testCase.isPrime;
            boolean actual = Prime.isPrime(testCase.num);

            if (expected) {
                assertTrue(testCase.num + " is prime", actual);
            } else {
                assertFalse(testCase.num + " is not prime", actual);
            }
        }
    }

    private static class TestCaseSpec {
        int num;
        boolean isPrime;

        public static TestCaseSpec make(int num, boolean isPrime) {
            TestCaseSpec testCase = new TestCaseSpec();
            testCase.isPrime = isPrime;
            testCase.num = num;
            return testCase;
        }
    }
}
```

### 个人总结：

```
public class Prime {
    public static boolean isPrime(int num) {
        return num > 1 && java.math.BigInteger.valueOf(num).isProbablePrime(20);
        // return num >= 0 && java.math.BigInteger.valueOf(num).isProbablePrime(42);
    }
}
```

```
import java.math.BigInteger;

public class Prime {
    public static boolean isPrime(int num) {

        if (num < 2) {
            return false;
        }

        BigInteger result = BigInteger.valueOf(num);
        return result.isProbablePrime((int) Math.log(num));
    }
}
```

```
public class Prime {
    public static boolean isPrime(int num) {
        if (num <= 1 || num != 2 && num % 2 == 0) {
            return false;
        }
        int sqprime = (int) Math.sqrt(num);
        for (int i = 3; i <= sqprime; i += 2) {
            if (num % i == 0) {
                return false;
            }
        }
        return true;
    }
}
```