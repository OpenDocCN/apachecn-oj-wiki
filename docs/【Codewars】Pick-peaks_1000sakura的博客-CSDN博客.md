<!--yml
category: codewars
date: 2022-08-13 11:50:26
-->

# 【Codewars】Pick peaks_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/90707239?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-90707239.nonecase](https://blog.csdn.net/ecysakura/article/details/90707239?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-90707239.nonecase)

### Codewars里的 5kyu Kata。

### 题目说明：

> In this kata, you will write a function that returns the positions and the values of the "peaks" (or local maxima) of a numeric array.
> 
> For example, the array `arr = [0, 1, 2, 5, 1, 0]` has a peak at position `3` with a value of `5`(since `arr[3]` equals `5`).
> 
> The output will be returned as a ``Map<String,List>`with two key-value pairs:`"pos"`and`"peaks"`. If there is no peak in the given array, simply return`{"pos" => [], "peaks" => []}`.
> 
> Example: `pickPeaks([3, 2, 3, 6, 4, 1, 2, 3, 2, 1, 2, 3])` should return `{pos: [3, 7], peaks: [6, 3]}` (or equivalent in other languages)
> 
> All input arrays will be valid integer arrays (although it could still be empty), so you won't need to validate the input.
> 
> The first and last elements of the array will not be considered as peaks (in the context of a mathematical function, we don't know what is after and before and therefore, we don't know if it is a peak or not).
> 
> Also, beware of plateaus !!! `[1, 2, 2, 2, 1]` has a peak while `[1, 2, 2, 2, 3]` does not. In case of a plateau-peak, please only return the position and value of the beginning of the plateau. For example: `pickPeaks([1, 2, 2, 2, 1])` returns `{pos: [1], peaks: [2]}` (or equivalent in other languages)
> 
> Have fun!

### 解题代码：

```
import java.util.Map;
import java.util.List;
import java.util.ArrayList;
import java.util.HashMap;

public class PickPeaks {

    public static Map<String,List<Integer>> getPeaks(int[] arr) {
        // Your code here!
        Map<String, List<Integer>> pos_peaks = new HashMap<String, List<Integer>>();
        List<Integer> pos = new ArrayList<Integer>();
        List<Integer> peaks = new ArrayList<Integer>();
        for(int i = 0; i<arr.length; i++) {
            if(i == 0 || i == arr.length-1) {
                continue;
            }else if(arr[i] > arr[i-1] && arr[i] > arr[i+1]) {
                pos.add(i);
                peaks.add(arr[i]);
            }else if(arr[i] > arr[i-1] && arr[i] == arr[i+1]) {
                for(int j = i; j<arr.length; j++) {
                    if(arr[j] < arr[i]) {
                        pos.add(i);
                        peaks.add(arr[i]);
                    }
                    if(arr[j] != arr[i]) {
                        i = j-1;
                        break;
                    }
                }
            }
        }
        pos_peaks.put("pos", pos);
        pos_peaks.put("peaks", peaks);

        return pos_peaks;
    }
}
```

Test Cases:

```
import org.junit.Test;
import static org.junit.Assert.assertEquals;
import org.junit.runners.JUnit4;
import java.util.*;
import java.util.stream.Collectors;

public class SolutionTest {

    private static String[] msg = { "should support finding peaks",
            "should support finding peaks, but should ignore peaks on the edge of the array",
            "should support finding peaks; if the peak is a plateau, it should only return the position of the first element of the plateau",
            "should support finding peaks; if the peak is a plateau, it should only return the position of the first element of the plateau",
            "should support finding peaks, but should ignore peaks on the edge of the array",
            "should support finding peaks, but should ignore peaks on the edge of the array",
            "should support finding peaks, despite the plateau", "should support finding peaks",
            "should return an object with empty arrays if the input is an empty array",
            "should return an object with empty arrays if the input does not contain any peak" };

    private static int[][] array = { { 1, 2, 3, 6, 4, 1, 2, 3, 2, 1 }, { 3, 2, 3, 6, 4, 1, 2, 3, 2, 1, 2, 3 },
            { 3, 2, 3, 6, 4, 1, 2, 3, 2, 1, 2, 2, 2, 1 }, { 2, 1, 3, 1, 2, 2, 2, 2, 1 }, { 2, 1, 3, 1, 2, 2, 2, 2 },
            { 2, 1, 3, 2, 2, 2, 2, 5, 6 }, { 2, 1, 3, 2, 2, 2, 2, 1 },
            { 1, 2, 5, 4, 3, 2, 3, 6, 4, 1, 2, 3, 3, 4, 5, 3, 2, 1, 2, 3, 5, 5, 4, 3 }, {}, { 1, 1, 1, 1 } };

    private static int[][] posS = { { 3, 7 }, { 3, 7 }, { 3, 7, 10 }, { 2, 4 }, { 2 }, { 2 }, { 2 }, { 2, 7, 14, 20 },
            {}, {} };

    private static int[][] peaksS = { { 6, 3 }, { 6, 3 }, { 6, 3, 2 }, { 3, 2 }, { 3 }, { 3 }, { 3 }, { 5, 6, 5, 5 },
            {}, {} };

    @Test
    public void sampleTests() {
        for (int n = 0; n < 5; n++) {
            final int[] p1 = posS[n], p2 = peaksS[n];
            Map<String, List<Integer>> expected = new HashMap<String, List<Integer>>() {
                {
                    put("pos", Arrays.stream(p1).boxed().collect(Collectors.toList()));
                    put("peaks", Arrays.stream(p2).boxed().collect(Collectors.toList()));
                }
            }, actual = PickPeaks.getPeaks(array[n]);
            assertEquals(msg[n], expected, actual);
        }
    }

    @Test
    public void moreTests() {
        for (int n = 5; n < msg.length; n++) {
            final int[] p1 = posS[n], p2 = peaksS[n];
            Map<String, List<Integer>> expected = new HashMap<String, List<Integer>>() {
                {
                    put("pos", Arrays.stream(p1).boxed().collect(Collectors.toList()));
                    put("peaks", Arrays.stream(p2).boxed().collect(Collectors.toList()));
                }
            }, actual = PickPeaks.getPeaks(array[n]);
            assertEquals(msg[n], expected, actual);
        }
    }

    private Random rand = new Random();

    @Test
    public void randomTests() {
        for (int n = 0; n < 40; n++) {

            int[] arr = new int[5 + rand.nextInt(25)];
            for (int i = 0; i < arr.length; i++)
                arr[i] = -5 + rand.nextInt(25);

            Map<String, List<Integer>> expected = SolPeaks.getPeaks(arr), actual = PickPeaks.getPeaks(arr);
            assertEquals(String.format("Testing for %s:", Arrays.toString(arr)), expected, actual);
        }
    }

    private static class SolPeaks {

        protected static Map<String, List<Integer>> getPeaks(int[] arr) {

            Map<String, List<Integer>> ans = new HashMap<String, List<Integer>>() {
                {
                    put("pos", new ArrayList<Integer>());
                    put("peaks", new ArrayList<Integer>());
                }
            };
            int posMax = 0;
            boolean matchAsc = false;

            for (int i = 1; i < arr.length; i++) {
                if (arr[i - 1] < arr[i]) {
                    matchAsc = true;
                    posMax = i;
                }
                if (matchAsc && arr[i - 1] > arr[i]) {
                    matchAsc = false;
                    ans.get("pos").add(posMax);
                    ans.get("peaks").add(arr[posMax]);
                }
            }
            return ans;
        }
    }

} 
```

### 个人总结：

```
import java.util.*;

public class PickPeaks {

    public static Map<String, List<Integer>> getPeaks(int[] arr) {

        Map<String, List<Integer>> ans = new HashMap<String, List<Integer>>() {
            {
                put("pos", new ArrayList<Integer>());
                put("peaks", new ArrayList<Integer>());
            }
        };
        int posMax = 0;
        boolean matchAsc = false;

        for (int i = 1; i < arr.length; i++) {
            if (arr[i - 1] < arr[i]) {
                matchAsc = true;
                posMax = i;
            }
            if (matchAsc && arr[i - 1] > arr[i]) {
                matchAsc = false;
                ans.get("pos").add(posMax);
                ans.get("peaks").add(arr[posMax]);
            }
        }
        return ans;
    }
}
```

```
import java.util.HashMap;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;
import java.util.stream.IntStream;

public class PickPeaks {

    public static Map<String, List<Integer>> getPeaks(int[] arr) {
        ArrayHelper arrayHelper = new ArrayHelper(arr);

        HashMap<String, List<Integer>> posPeaksMap = new HashMap<>();

        List<Integer> pos = IntStream.range(1, arr.length).filter(arrayHelper::isPeak).boxed()
                .collect(Collectors.toList());

        List<Integer> peaks = pos.stream().map(i -> arr[i]).collect(Collectors.toList());

        posPeaksMap.put("pos", pos);
        posPeaksMap.put("peaks", peaks);

        return posPeaksMap;
    }

    private static class ArrayHelper {

        private final int[] array;

        private ArrayHelper(int[] array) {
            this.array = array;
        }

        boolean isPeak(int index) {
            return isBiggerThanDirectPredecessor(index) && isBiggerThanAnySuccessor(index);
        }

        private boolean isBiggerThanDirectPredecessor(int index) {
            return array[index] > array[index - 1];
        }

        private boolean isBiggerThanAnySuccessor(int index) {
            int value = array[index];

            for (int succeedingIndex = index + 1; succeedingIndex < array.length; succeedingIndex++) {
                int succeedingValue = array[succeedingIndex];

                if (value == succeedingValue) {
                    continue;
                }

                return value > succeedingValue;
            }

            return false;
        }

    }

}
```

```
import java.util.*;

public class PickPeaks {

    public static Map<String, List<Integer>> getPeaks(int[] array) {

        List<Integer> maxima = new ArrayList<>();
        List<Integer> positions = new ArrayList<>();
        Map<String, List<Integer>> map = new HashMap<>();

        // Input array must have atleast 3 elements in order to find a local maxima.
        if (array.length < 3) {
            map.put("peaks", maxima);
            map.put("pos", positions);
            return map;
        }
        int front, middle = array[0], end = array[1], index = 2, plateauStartPoint = 1, plateauEndPoint,
                dupeCounter = 0, dupeValue = array[1];

        while (index < array.length) {

            front = middle;
            middle = end;
            end = array[index];

            if (dupeValue == array[index])
                dupeCounter++;
            else {
                dupeCounter = 0;
                plateauStartPoint = index;
            }
            dupeValue = array[index];

            // Comparing the middle value with it's neighbours to see if it is the local
            // maxima.
            if (middle > front && middle > end) {
                maxima.add(middle);
                positions.add(index - 1);
            }
            /*
             * DupeCounter will only ever register as more than 0 if a consectutive
             * duplicate occur. If a consectutive duplicate is detected then it could imply
             * a plateau.
             */
            if (dupeCounter >= 1) {
                /*
                 * Set the end of the suspected plateau as the index of the next element if
                 * there is one else set as end of array
                 */
                plateauEndPoint = ((index + 1) >= (array.length)) ? index : (index + 1);

                /*
                 * The start of the plateau will be index of the first element of the
                 * consectutive duplicates. all the duplicates are treated as one and checked
                 * against it's immediate neighbours.
                 */
                if (array[plateauStartPoint - 1] < dupeValue && array[plateauEndPoint] < dupeValue) {
                    maxima.add(dupeValue);
                    positions.add(plateauStartPoint);
                    dupeCounter = 0;
                }
            }
            index++;
        }
        map.put("peaks", maxima);
        map.put("pos", positions);
        return map;
    }
}
```

```
import static java.util.stream.Collectors.toList;

import java.util.ArrayList;
import java.util.Map;
import java.util.List;

public class PickPeaks {
    public static Map<String, List<Integer>> getPeaks(int[] arr) {
        List<Integer> pos = new ArrayList<>();
        boolean ascending = false;
        int localPeakPos = -1;

        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > arr[i - 1]) {
                ascending = true;
                localPeakPos = i;
            }
            if (arr[i] < arr[i - 1] && ascending) {
                pos.add(localPeakPos);
                ascending = false;
            }
        }

        return Map.of("pos", pos, "peaks", pos.stream().map(i -> arr[i]).collect(toList()));
    }
}
```

```
def pick_peaks(arr):
    peak, pos = [], []
    res = { "peaks":[], "pos":[] }
    for i in range(1, len(arr)) :
        if arr[i]>arr[i-1] :
            peak, pos = [arr[i]], [i]
        elif arr[i]<arr[i-1] :
            res["peaks"] += peak
            res["pos"] += pos
            peak, pos = [], []
    return res
```

一个压栈出栈的思路。