<!--yml
category: codewars
date: 2022-08-13 11:48:57
-->

# 【Codewars】Find The Parity Outlier_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/90707121?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-90707121.nonecase](https://blog.csdn.net/ecysakura/article/details/90707121?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-90707121.nonecase)

### Codewars里的 6kyu Kata。

### 题目说明：

> You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer `N`. Write a method that takes the array as an argument and returns this "outlier" `N`.
> 
> ## Examples
> 
> ```
> [2, 4, 0, 100, 4, 11, 2602, 36]
> Should return: 11 (the only odd number)
> 
> [160, 3, 1719, 19, 11, 13, -21]
> Should return: 160 (the only even number)
> ```

### 解题代码：

```
public class FindOutlier{
    static int find(int[] integers){
        int i = 0, j = integers.length - 1;
        if(Math.abs(integers[i])%2 != Math.abs(integers[j])%2) {// 不同
            i++;
            if(Math.abs(integers[i])%2 == Math.abs(integers[j])%2) {// 进一步判断相同
                return integers[i-1];
            }
            j--;
            if(Math.abs(integers[i])%2 == Math.abs(integers[j])%2) {
                return integers[j+1];
            }
        }

        while(i < j) {
            if(Math.abs(integers[i])%2 != Math.abs(integers[j])%2) {
                if(Math.abs(integers[i])%2 == Math.abs(integers[0])%2) {
                    return integers[j];
                }else {
                    return integers[i];
                }
            }
            i++;
            j--;
        }

        return integers[i];
    }
}
```

Test Cases:

```
import org.junit.Test;
import static org.junit.Assert.assertEquals;
import org.junit.runners.JUnit4;
import java.util.Random;

public class OutlierTest {
    @Test
    public void test() {
        /* Basic tests */

        int[] ints1 = { 2, 6, 8, 10, 3 }; // odd at the back
        int[] ints2 = { 2, 6, 8, 200, 700, 1, 84, 10, 4 }; // odd in the middle
        int[] ints3 = { 17, 6, 8, 10, 6, 12, 24, 36 }; // odd in the front
        int[] ints4 = { 2, 1, 7, 17, 19, 211, 7 }; // even in the front
        int[] ints5 = { 1, 1, 1, 1, 1, 44, 7, 7, 7, 7, 7, 7, 7, 7 }; // even in the middle
        int[] ints6 = { 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 35, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 7, 7, 7, 7, 1000 }; // even
                                                                                                                        // at
                                                                                                                        // the
                                                                                                                        // end
        int[] ints7 = { 2, -6, 8, -10, -3 }; // odd at the back, negative
        int[] ints8 = { 2, 6, 8, 2, -66, 34, -35, 66, 700, 1002, -84, 10, 4 }; // odd in the middle, negative
        int[] ints9 = { -1 * Integer.MAX_VALUE, -18, 6, -8, -10, 6, 12, -24, 36 }; // odd in the front, negative
        int[] ints10 = { -20, 1, 7, 17, 19, 211, 7 }; // even in the front, negative
        int[] ints11 = { 1, 1, -1, 1, 1, -44, 7, 7, 7, 7, 7, 7, 7, 7 }; // even in the middle, negative
        int[] ints12 = { 1, 0, 0 }; // odd answer, zeroes
        int[] ints13 = { 3, 7, -99, 81, 90211, 0, 7 }; // even in the middle, zero

        assertEquals(3, FindOutlier.find(ints1));
        assertEquals(1, FindOutlier.find(ints2));
        assertEquals(17, FindOutlier.find(ints3));
        assertEquals(2, FindOutlier.find(ints4));
        assertEquals(44, FindOutlier.find(ints5));
        assertEquals(1000, FindOutlier.find(ints6));
        assertEquals(-3, FindOutlier.find(ints7));
        assertEquals(-35, FindOutlier.find(ints8));
        assertEquals(-1 * Integer.MAX_VALUE, FindOutlier.find(ints9));
        assertEquals(-20, FindOutlier.find(ints10));
        assertEquals(-44, FindOutlier.find(ints11));
        assertEquals(1, FindOutlier.find(ints12));
        assertEquals(0, FindOutlier.find(ints13));
        // Random tests
        Random r = new Random();
        int positionA = r.nextInt(400);
        int positionB = r.nextInt(400);
        int[] randomOdds = new int[400];
        int[] randomEvens = new int[400];
        int evenSample = r.nextInt(3000) * 2;
        int oddSample = r.nextInt(3000) * 2 + 1;
        for (int i = 0; i < 400; i++) {
            randomOdds[i] = r.nextInt(3000) * 2 + 1;
        }
        for (int i = 0; i < 400; i++) {
            randomEvens[i] = r.nextInt(3000) * 2;
        }
        randomOdds[positionA] = evenSample;
        randomEvens[positionB] = oddSample;

        assertEquals(evenSample, FindOutlier.find(randomOdds));
        assertEquals(oddSample, FindOutlier.find(randomEvens));
        // large array test
        int positionC = r.nextInt(10000000);
        int positionD = r.nextInt(10000000);
        int[] bigOddArray = new int[10000000];
        int[] bigEvenArray = new int[10000000];
        for (int i = 0; i < 10000000; i++) {
            bigOddArray[i] = r.nextInt(100000) * 2 + 1;
            bigEvenArray[i] = r.nextInt(100000) * 2;
        }
        bigOddArray[positionC] = evenSample;
        bigEvenArray[positionD] = oddSample;
        assertEquals(evenSample, FindOutlier.find(bigOddArray));
        assertEquals(oddSample, FindOutlier.find(bigEvenArray));
    }
}
```

### 个人总结：

```
import java.util.Arrays;

public class FindOutlier {
    public static int find(int[] integers) {
        // Since we are warned the array may be very large, we should avoid counting
        // values any more than we need to.

        // We only need the first 3 integers to determine whether we are chasing odds or
        // evens.
        // So, take the first 3 integers and compute the value of Math.abs(i) % 2 on
        // each of them.
        // It will be 0 for even numbers and 1 for odd numbers.
        // Now, add them. If sum is 0 or 1, then we are chasing odds. If sum is 2 or 3,
        // then we are chasing evens.
        int sum = Arrays.stream(integers).limit(3).map(i -> Math.abs(i) % 2).sum();
        int mod = (sum == 0 || sum == 1) ? 1 : 0;

        return Arrays.stream(integers).parallel() // call parallel to get as much bang for the buck on a "large" array
                .filter(n -> Math.abs(n) % 2 == mod).findFirst().getAsInt();
    }
}
```

```
public class FindOutlier {

    static int find(int[] integers) {
        int oddcount = 0, odd = 0, evencount = 0, even = 0;
        for (int i : integers) {
            if (i % 2 == 0) {
                even = i;
                evencount++;
            } else {
                odd = i;
                oddcount++;
            }
            if (evencount > 0 && oddcount > 0) {
                if (evencount > 1) {
                    return odd;
                } else if (oddcount > 1) {
                    return even;
                }
            }
        }
        return evencount > 1 ? odd : even;
    }
}
```

```
import java.util.Arrays;

public class FindOutlier {
    static int find(int[] integers) {
        int[] array = Arrays.stream(integers).filter(i -> i % 2 == 0).toArray();
        return array.length == 1 ? array[0] : Arrays.stream(integers).filter(i -> i % 2 != 0).findAny().getAsInt();
    }
}
```

```
public class FindOutlier {
    static int find(int[] integers) {
        int even = 0;
        int odd = 0;
        int cycle = 0;

        for (Integer value : integers) {
            if (value % 2 == 0) {
                cycle++;
                even = value;
            } else {
                odd = value;
            }
        }
        return (cycle > 1) ? odd : even;
    }
}
```