<!--yml
category: codewars
date: 2022-08-13 11:51:41
-->

# 【Codewars】Maximum subarray sum_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/90378315?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-90378315.nonecase](https://blog.csdn.net/ecysakura/article/details/90378315?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-90378315.nonecase)

### Codewars里的 5kyu Kata。

### 题目说明：

> The maximum sum subarray problem consists in finding the maximum sum of a contiguous subsequence in an array or list of integers:
> 
> ```
> Max.sequence(new int[]{-2, 1, -3, 4, -1, 2, 1, -5, 4});
> // should be 6: {4, -1, 2, 1}
> ```
> 
> Easy case is when the list is made up of only positive numbers and the maximum sum is the sum of the whole array. If the list is made up of only negative numbers, return 0 instead.
> 
> Empty list is considered to have zero greatest sum. Note that the empty list or array is also a valid sublist/subarray.

动态规划题目，总感觉在哪里见过？求的是连续最大和的值，如果不熟悉动态规划的话，可以尝试使用二维数组解题，也是一种不错的锻炼。

### 解题代码：

```
public class Max {
    public static int sequence(int[] arr) {
        int len = arr.length;
        if (len == 0)
            return 0;
        if (len == 1)
            return arr[0] > 0 ? arr[0] : 0;
        // int[] dp = new int[len];
        // dp[0] = arr[0] > 0 ? arr[0] : 0;
        int dp = arr[0] > 0 ? arr[0] : 0;
        int max = arr[0] > 0 ? arr[0] : 0;

        for (int i = 1; i < len; i++) {
            if (arr[i] > 0) {
                // dp[i] = arr[i] + dp[i - 1];
                dp += arr[i];
            } else {
                // max = max > dp[i - 1] ? max : dp[i -1];
                // dp[i] = dp[i - 1] + arr[i] > 0 ? dp[i - 1] + arr[i] : 0;
                max = max > dp ? max : dp;
                dp = dp + arr[i] > 0 ? dp + arr[i] : 0;
            }
        }
        // return max > dp[len - 1] ? max : dp[len - 1];
        return max = max > dp ? max : dp;
    }
}
```

Test Cases:

```
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class MaxSequenceTest {
    @Test
    public void testEmptyArray() throws Exception {
        assertEquals("Empty arrays should have a max of 0", 0, Max.sequence(new int[] {}));
    }

    @Test
    public void testExampleArray() throws Exception {
        assertEquals("Example array should have a max of 6", 6,
                Max.sequence(new int[] { -2, 1, -3, 4, -1, 2, 1, -5, 4 }));
    }

    @Test
    public void testNegativeExampleArray() throws Exception {
        assertEquals("Example array with all negative values should have a max of 0", 0,
                Max.sequence(new int[] { -2, -1, -3, -4, -1, -2, -1, -5, -4 }));
    }

    @Test
    public void testRandomArrays() throws Exception {
        for (int i = 0; i < 50; i++) {
            int[] rand = randArr((int) (Math.random() * 10 + 50));
            assertEquals("Random array solution not as expected: ", solution(rand), Max.sequence(rand));
        }
    }

    private int[] randArr(int size) {
        int[] rand = new int[size];
        for (int i = 0; i < size; i++)
            rand[i] = (int) (Math.random() * 60 - 30);
        return rand;
    }

    private int solution(int[] arr) {
        int m = 0, a = 0, s = 0;
        for (int e : arr) {
            s += e;
            m = Math.min(s, m);
            a = Math.max(a, s - m);
        }
        return a;
    }
}
```

### 个人总结：

动态规划数组被我替换成了一个值，节省了内存空间。