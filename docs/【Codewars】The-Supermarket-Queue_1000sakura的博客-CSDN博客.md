<!--yml
category: codewars
date: 2022-08-13 11:35:27
-->

# 【Codewars】The Supermarket Queue_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/90315905?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058616781685360739%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058616781685360739&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-90315905-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/ecysakura/article/details/90315905?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058616781685360739%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058616781685360739&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-90315905-null-null.142^v40^control,185^v2^control&utm_term=codewars)

### Codewars里的 6kyu Kata。

### 题目说明：

> There is a queue for the self-checkout tills at the supermarket. Your task is write a function to calculate the total time required for all the customers to check out!
> 
> * * *
> 
> The function has two input variables:
> 
> *   customers: an array (list in python) of positive integers representing the queue. Each integer represents a customer, and its value is the amount of time they require to check out.
> *   n: a positive integer, the number of checkout tills.
> 
> The function should return an integer, the total time required.
> 
> * * *
> 
> EDIT: A lot of people have been confused in the comments. To try to prevent any more confusion:
> 
> *   There is only ONE queue, and
> *   The order of the queue NEVER changes, and
> *   Assume that the front person in the queue (i.e. the first element in the array/list) proceeds to a till as soon as it becomes free.
> *   The diagram on the wiki page I linked to at the bottom of the description may be useful.
> 
> So, for example:
> 
> ```
> queueTime([5,3,4], 1)
> // should return 12
> // because when n=1, the total time is just the sum of the times
> 
> queueTime([10,2,3,3], 2)
> // should return 10
> // because here n=2 and the 2nd, 3rd, and 4th people in the 
> // queue finish before the 1st person has finished.
> 
> queueTime([2,3,10], 2)
> // should return 12
> ```
> 
> N.B. You should assume that all the test input will be valid, as specified above.
> 
> P.S. The situation in this kata can be likened to the more-computer-science-related idea of a thread pool, with relation to running multiple processes at the same time: [https://en.wikipedia.org/wiki/Thread_pool](https://en.wikipedia.org/wiki/Thread_pool)

题目简单，等同于排队接水问题，思路有了，但是自己写的代码却不尽人意。主要的问题在于中间 0 值的判断，如果把数组重构为链表的话回更简单点。

### 解题代码：

```
import java.util.Arrays;

public class Solution {

    public static int solveSuperMarketQueue(int[] customers, int n) {
        int len = customers.length;
        if (len == 0 || n == 0)
            return 0;
        int res = 0;

        // 如果人数过少, 直接取最大值
        if (len < n) {
            res = customers[0];
            for (int i = 1; i < len; i++) {
                if (customers[i] > res)
                    res = customers[i];
            }
            return res;
        }

        int start = 0, end = n;
        while (end < len) {
            int min = customers[start];
            for (int i = start + 1; i < end; i++) {
                if (customers[i] > 0 && min > customers[i])
                    min = customers[i];
            }

            res += min;
            for (int i = start; i < end; i++) {
                if (customers[i] != 0)
                    customers[i] -= min;
            }

            while (customers[start] == 0) {
                start++;
            }

            int k = 1;
            int count = 1;

            // 非0值计数
            while (count < n) {
                if (start + k >= len) {
                    end = start + k;
                    break;
                }
                if (customers[start + k] != 0)
                    count++;
                k++;
            }

            end = start + k;
        }

        // 最后一组取最大值
        int max = customers[start];
        for (int i = start + 1; i < len; i++) {
            if (customers[i] > max)
                max = customers[i];
        }
        res += max;
        return res;
    }

}
```

Test Cases:

```
import org.junit.Test;
import static org.junit.Assert.assertEquals;
import org.junit.runners.JUnit4;

import java.util.Arrays;
import java.lang.*;
import java.util.Random;

public class SolutionTest {
    @Test
    public void testNormalCondition() {
        assertEquals(9, Solution.solveSuperMarketQueue(new int[] { 2, 2, 3, 3, 4, 4 }, 2));
    }

    @Test
    public void testEmptyArray() {
        assertEquals(0, Solution.solveSuperMarketQueue(new int[] {}, 1));
    }

    @Test
    public void testBigN() {
        assertEquals(5, Solution.solveSuperMarketQueue(new int[] { 1, 2, 3, 4, 5 }, 100));
    }

    @Test
    public void testSingleCustomer() {
        assertEquals(2, Solution.solveSuperMarketQueue(new int[] { 2 }, 5));
    }

    @Test
    public void testSingleCustomerSingleTill() {
        assertEquals(5, Solution.solveSuperMarketQueue(new int[] { 5 }, 1));
    }

    @Test
    public void testSingleTillManyCustomers() {
        assertEquals(15, Solution.solveSuperMarketQueue(new int[] { 1, 2, 3, 4, 5 }, 1));
    }

    @Test
    public void testLongCustomerArray() {
        assertEquals(113, Solution.solveSuperMarketQueue(
                new int[] { 29, 18, 6, 23, 25, 29, 24, 17, 10, 8, 8, 22, 20, 16, 13, 17, 7, 21, 7, 11, 18, 26, 25, 1,
                        18, 29, 16, 26, 7, 11, 13, 20, 12, 6, 23, 3, 10, 9, 8, 5, 6, 18, 19, 26, 5, 15, 4, 15, 1, 4 },
                7));
    }

    @Test
    public void testRandomValues() {
        final int max_tills = 6;
        Random rand = new Random();
        for (int l = 0; l < 2; l++) {
            int n = rand.nextInt(max_tills) + 1;
            int[] list = generateRandomArray();
            for (int j = 0; j < 3; j++) {
                n = ((n + j) % max_tills) + 1;
                System.out.println("Testing n: " + n + ", array: " + stringifiedArray(list));
                assertEquals(MySolution.solveSuperMarketQueue(list, n), Solution.solveSuperMarketQueue(list, n));
            }
        }
    }

    public int[] generateRandomArray() {
        final int max_elements = 25;
        final int max_single_value = 7;
        Random rand = new Random();
        int size = rand.nextInt(max_elements) + 1;
        int[] list = new int[size];
        for (int i = 0; i < size; i++) {
            list[i] = rand.nextInt(max_single_value) + 1;
        }
        return list;
    }

    public String stringifiedArray(int[] arr) {
        StringBuilder sb = new StringBuilder();
        sb.append("[");
        for (int i = 0; i < arr.length; i++) {
            sb.append("" + arr[i]);
            if (i != arr.length - 1) {
                sb.append(",");
            }
        }
        sb.append("]");
        return sb.toString();
    }

    public static class MySolution {
        // Because screw streams, that's why!
        public static int getArrayIndex(int[] arr, int value) {
            int k = 0;
            for (int i = 0; i < arr.length; i++) {
                if (arr[i] == value) {
                    k = i;
                    break;
                }
            }
            return k;
        }

        public static int solveSuperMarketQueue(int[] customers, int n) {
            // I want to be explicit about it
            if (customers.length == 0) {
                return 0;
            }
            int i = n;
            // I want to use primitive int, problems?
            int ssize = Math.min(customers.length, n);
            int[] sample = new int[ssize];
            for (int j = 0; j < ssize; j++) {
                sample[j] = customers[j];
            }
            while (i < customers.length) {
                int mmin = Arrays.stream(sample).min().getAsInt();
                int idx = getArrayIndex(sample, mmin);
                sample[idx] += customers[i];
                i++;
            }
            int mmax = Arrays.stream(sample).max().getAsInt();
            return mmax;
        }
    }

}
```

### 个人总结：

重点在于中间的 0 值判断，写了几次都没把握好，代码可以优化。

另一种参考代码：

```
import java.util.Arrays;

public class Solution {

    public static int solveSuperMarketQueue(int[] customers, int n) {
        int[] result = new int[n];
        for (int i = 0; i < customers.length; i++) {
            result[0] += customers[i];
            Arrays.sort(result);
        }
        return result[n - 1];
    }

}
```

利用内置排序对 result 进行动态计算。算是一种很好理解的代码。

运用工具包解题：

```
import java.util.Collections;
import java.util.PriorityQueue;

public class Solution {

    public static int solveSuperMarketQueue(int[] customers, int n) {
        PriorityQueue<Integer> q = new PriorityQueue<>();
        for (int i = 0; i < n; i++)
            q.add(0);
        for (int t : customers)
            q.add(q.remove() + t);
        return Collections.max(q);
    }

}
```

不限于使用 PriorityQueue 解题，可以使用动态数组，只是不好操作。

链表解题：

```
import java.util.*;
import java.util.stream.IntStream;

public class Solution {

    private static List<Integer> tills;
    private static int time;
    private static List<Integer> queue;

    public static int solveSuperMarketQueue(int[] customers, int n) {
        initialize(customers, n);
        while (anyCustomersLeft()) {
            assignCustomersToAllFreeTills();
            progressTime();
        }
        while (anyTillHasCustomer()) {
            progressTime();
        }
        return time;
    }

    private static void initialize(int[] customers, int n) {
        tills = new ArrayList<>(Collections.nCopies(n, 0));
        queue = new ArrayList<>();
        IntStream.range(0, customers.length).forEach(i -> queue.add(customers[i]));
        time = 0;
    }

    private static void assignCustomersToAllFreeTills() {
        OptionalInt freeTill = findFreeTill();
        while (anyCustomersLeft() && freeTill.isPresent()) {
            assignNextCustomerToTill(freeTill.getAsInt());
            freeTill = findFreeTill();
        }
    }

    private static boolean anyCustomersLeft() {
        return !queue.isEmpty();
    }

    private static OptionalInt findFreeTill() {
        return IntStream.range(0, tills.size()).filter(i -> tills.get(i) == 0).findFirst();
    }

    private static void assignNextCustomerToTill(int tillNumber) {
        tills.set(tillNumber, queue.get(0));
        queue.remove(0);
    }

    private static void progressTime() {
        IntStream.range(0, tills.size()).filter(till -> isTillNotEmpty(till)).forEach(till -> decreaseTillTime(till));
        time++;
    }

    private static boolean isTillNotEmpty(int tillNumber) {
        return tills.get(tillNumber) != 0;
    }

    private static void decreaseTillTime(int tillNumber) {
        tills.set(tillNumber, tills.get(tillNumber) - 1);
    }

    private static boolean anyTillHasCustomer() {
        return tills.stream().anyMatch(i -> i != 0);
    }
}
```

很强！