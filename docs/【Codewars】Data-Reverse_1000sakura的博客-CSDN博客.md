<!--yml
category: codewars
date: 2022-08-13 11:50:33
-->

# 【Codewars】Data Reverse_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/90606109?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-90606109.nonecase](https://blog.csdn.net/ecysakura/article/details/90606109?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-90606109.nonecase)

### Codewars里的 6kyu Kata。

### 题目说明：

> Description:
> 
> A stream of data is received and needs to be reversed.
> 
> Each segment is 8 bits long, meaning the order of these segments needs to be reversed, for example:
> 
> ```
> 11111111  00000000  00001111  10101010
>  (byte1)   (byte2)   (byte3)   (byte4)
> ```
> 
> should become:
> 
> ```
> 10101010  00001111  00000000  11111111
>  (byte4)   (byte3)   (byte2)   (byte1)
> ```
> 
> The total number of bits will always be a multiple of 8.
> 
> The data is given in an array as such:
> 
> ```
> [1,1,1,1,1,1,1,1,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,1,1,0,1,0,1,0,1,0]
> ```

### 解题代码：

```
import java.util.Arrays;

public class Kata {
    public static int[] DataReverse(int[] data) {
        int i = 0, j = data.length - 8;
        int[] res = new int[data.length];

        while(j > i) {
            for(int k = 0; k < 8; k++) {
                res[j+k] = data[i+k];
                res[i+k] = data[j+k];
            }
            i+=8;
            j-=8;
        }
        return res;
    }
}
```

Test Cases:

```
import java.util.*;
import org.junit.Test;
import static org.junit.Assert.assertArrayEquals;

public class ReverseTest {

    public static int[] rando(int num) {

        // Picks between 0 and 1
        int[] arr = new int[num];
        int[] bit = { 0, 1 };
        java.util.Random random = new java.util.Random();

        // Makes array with 0's and 1's
        for (int i = 0; i < num; i++) {
            arr[i] = random.nextInt(bit.length);
        }
        return arr;
    }

    public static int[] answer(int[] data) {
        int len = data.length;
        int[] out = new int[len];

        for (int i = 0; i < len; i = i + 8) {
            out[i] = data[len - i - 8];
            out[i + 1] = data[len - i - 7];
            out[i + 2] = data[len - i - 6];
            out[i + 3] = data[len - i - 5];
            out[i + 4] = data[len - i - 4];
            out[i + 5] = data[len - i - 3];
            out[i + 6] = data[len - i - 2];
            out[i + 7] = data[len - i - 1];
        }
        return out;
    }

    @Test
    public void Tests() {
        int[] data1 = { 0, 1, 0, 1, 0, 1, 0, 1, 1, 0, 1, 0, 1, 0, 1, 0 };
        int[] data2 = { 1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 0, 1, 0, 1, 0, 1 };
        assertArrayEquals(data2, Kata.DataReverse(data1));

        int[] data3 = { 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 1, 1,
                1 };
        int[] data4 = { 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0,
                0 };
        assertArrayEquals(data4, Kata.DataReverse(data3));
    }

    @Test
    public void RandomTests() {
        int[] data5 = rando(16);
        assertArrayEquals(Kata.DataReverse(data5), ReverseTest.answer(data5));
        data5 = rando(32);
        assertArrayEquals(Kata.DataReverse(data5), ReverseTest.answer(data5));
        data5 = rando(48);
        assertArrayEquals(Kata.DataReverse(data5), ReverseTest.answer(data5));
        data5 = rando(64);
        assertArrayEquals(Kata.DataReverse(data5), ReverseTest.answer(data5));
        data5 = rando(48);
        assertArrayEquals(Kata.DataReverse(data5), ReverseTest.answer(data5));
        data5 = rando(32);
        assertArrayEquals(Kata.DataReverse(data5), ReverseTest.answer(data5));
        data5 = rando(16);
        assertArrayEquals(Kata.DataReverse(data5), ReverseTest.answer(data5));
        data5 = rando(32);
        assertArrayEquals(Kata.DataReverse(data5), ReverseTest.answer(data5));
        data5 = rando(48);
        assertArrayEquals(Kata.DataReverse(data5), ReverseTest.answer(data5));
        data5 = rando(64);
        assertArrayEquals(Kata.DataReverse(data5), ReverseTest.answer(data5));
    }
}
```

### 个人总结：

```
public class Kata {
    public static int[] DataReverse(int[] data) {
        return java.util.stream.IntStream.range(0, data.length).map(i -> data[data.length - 8 - (i / 8 * 8) + (i % 8)])
                .toArray();
    }
}
```

```
public class Kata {
    public static int[] DataReverse(int[] data) {
        int bytes[] = new int[data.length];
        for (int i = data.length - 8, j = 0; i >= 0; i -= 8, j += 8) {
            System.arraycopy(data, i, bytes, j, 8);
        }
        return bytes;
    }
}
```

```
public class Kata {
    public static int[] DataReverse(int[] data) {
        int[] reversed = new int[data.length];
        for (int i = 0; i < data.length; i += 8) {
            System.arraycopy(data, i, reversed, data.length - 8 - i, 8);
        }
        return reversed;
    }
}
```

```
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;

public class Kata {
    public static int[] DataReverse(int[] data) {
        ArrayList<int[]> myList = new ArrayList<>();

        for (int i = 0; i < data.length; i = i + 8) {
            myList.add(Arrays.copyOfRange(data, i, i + 8));
        }

        Collections.reverse(myList);

        return myList.stream().flatMapToInt(i -> Arrays.stream(i)).toArray();
    }
}
```

这道题不能使用原地算法：

```
import java.util.Arrays;

public class Kata {
    public static int[] DataReverse(int[] data) {
        int i = 0, j = data.length - 8;
        if(j < 0)return new int[] {0};

        int temp;
        while(j > i) {
            for(int k = 0; k < 8; k++) {
                temp = data[i+k];
                data[i+k] = data[j+k];
                data[j+k] = temp;
            }
            i+=8;
            j-=8;
        }
        return data;
    }
}
```