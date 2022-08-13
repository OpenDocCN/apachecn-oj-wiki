<!--yml
category: codewars
date: 2022-08-13 11:47:43
-->

# 【Codewars】All Inclusive?_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/90603835?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-90603835.nonecase](https://blog.csdn.net/ecysakura/article/details/90603835?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-90603835.nonecase)

### Codewars里的 7kyu Kata。

### 题目说明：

> Description:
> 
> Input:
> 
> *   a string `strng`
> *   an array of strings `arr`
> 
> Output of function `contain_all_rots(strng, arr) (or containAllRots or contain-all-rots)`:
> 
> *   a boolean `true` if all rotations of `strng` are included in `arr` (C returns 1)
> *   `false` otherwise (C returns 0)
> 
> ## Examples:
> 
> ```
> contain_all_rots(
>   "bsjq", ["bsjq", "qbsj", "sjqb", "twZNsslC", "jqbs"]) -> true
> 
> contain_all_rots(
>   "Ajylvpy", ["Ajylvpy", "ylvpyAj", "jylvpyA", "lvpyAjy", "pyAjylv", "vpyAjyl", "ipywee"]) -> false)
> ```
> 
> ## Note:
> 
> Though not correct in a mathematical sense
> 
> *   we will consider that there are no rotations of `strng == ""`
> *   and for any array `arr`: `contain_all_rots("", arr) --> true`
> 
> Ref: [https://en.wikipedia.org/wiki/String_(computer_science)#Rotations](https://en.wikipedia.org/wiki/String_%28computer_science%29#Rotations)

### 解题代码：

```
import java.util.List;
import java.util.ArrayList;

public class Rotations {

    public static boolean containAllRots(String strng, List<String> arr) {
        // your code
        StringBuilder sb = new StringBuilder(strng);
        List<String> sl = new ArrayList<>();

        for(int i = 0; i < sb.length(); i++){
            String temp = sb.substring(0, 1);
            for(int j = 0; j < sb.length(); j++){
                if(j < sb.length() - 1){
                    sb.replace(j, j+1, sb.substring(j+1, j+2));
                }else{
                    sb.replace(j, j+1, temp);
                }
            }
            sl.add(sb.toString());
        }

        boolean result = true;
        for(String item : sl){
            result = result & arr.contains(item);
        }

        return result;
    }
}
```

Test Cases:

```
import static org.junit.Assert.*;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.HashSet;
import java.util.List;
import java.util.Set;
import org.junit.Test;

public class RotationsTest {
    private static void testing(Boolean actual, Boolean expected) {
        assertEquals(expected, actual);
    }

    @Test
    public void test() {
        System.out.println("Fixed Tests containAllRots");
        List<String> a = Arrays.asList("bsjq", "qbsj", "sjqb", "twZNsslC", "jqbs");
        testing(Rotations.containAllRots("bsjq", a), true);
        a = Arrays.asList("TzYxlgfnhf", "yqVAuoLjMLy", "BhRXjYA", "YABhRXj", "hRXjYAB", "jYABhRX", "XjYABhR",
                "ABhRXjY");
        testing(Rotations.containAllRots("XjYABhR", a), false);
        a = Arrays.asList("hQmSQJA", "QJAhQmS", "QmSQJAh", "yUgUXoQE", "AhQmSQJ", "mSQJAhQ", "SQJAhQm", "JAhQmSQ");
        testing(Rotations.containAllRots("QJAhQmS", a), true);
        a = Arrays.asList("nVOETcaxdvuk", "shpEts", "hpEtss", "Etsshp", "OuIiQ", "sXrDdPXIaW", "tsshpE", "pEtssh");
        testing(Rotations.containAllRots("Etsshp", a), false);
        a = Arrays.asList("Ajylvpy", "ylvpyAj", "jylvpyA", "lvpyAjy", "pyAjylv", "vpyAjyl");
        testing(Rotations.containAllRots("Ajylvpy", a), false);
        a = Arrays.asList("numMfygcH", "HFMqhWv", "qhWvHFM", "ZJKKxM", "hWvHFMq", "MqhWvHF", "hfZWYSqk", "BTcSoEdchPlL",
                "WvHFMqh", "vHFMqhW", "FMqhWvH");
        testing(Rotations.containAllRots("MqhWvHF", a), true);
        a = Arrays.asList("vGUD", "UDvG", "GUDv", "DvGU");
        testing(Rotations.containAllRots("UDvG", a), true);
        a = Arrays.asList("ObPfws", "Cofuhqrmmzq", "wFvfcqU", "sObPfw", "bPfwsO", "PfwsOb", "wsObPf", "fwsObP");
        testing(Rotations.containAllRots("sObPfw", a), true);
        a = Arrays.asList("MKUck", "EDjfbQB", "GUPwzk", "SKZvilwnL", "UckMK", "KUckM", "kMKUc");
        testing(Rotations.containAllRots("KUckM", a), false);
        a = Arrays.asList("DIeF", "IeFD", "FDIe", "eFDI");
        testing(Rotations.containAllRots("FDIe", a), true);
        a = Arrays.asList("DIeF", "IeFD", "12341234", "41234123", "34123412", "23412341");
        testing(Rotations.containAllRots("12341234", a), true);
    }

    ///
    private static int randInt(int min, int max) {
        return (int) (min + Math.random() * ((max - min) + 1));
    }

    private static List<String> rotationsArraySol(String strng) {
        List<String> result = new ArrayList<String>();
        for (int index = 0; index < strng.length(); index++) {
            String rotatedString = strng.substring(index) + strng.substring(0, index);
            if (result.contains(rotatedString) == false)
                result.add(rotatedString);
        }
        return result;
    }

    private static Set<String> rotationsSol(String strng) {
        Set<String> result = new HashSet<String>();
        for (int index = 0; index < strng.length(); index++) {
            String rotatedString = strng.substring(index) + strng.substring(0, index);
            if (result.contains(rotatedString) == false)
                result.add(rotatedString);
        }
        return result;
    }

    private static Boolean containAllRotsSol(String strng, List<String> arr) {
        Set<String> setarr = new HashSet<String>(arr);
        Set<String> result = rotationsSol(strng);
        Set<String> intersect = new HashSet<String>(setarr);
        intersect.retainAll(result);
        return intersect.equals(result);
    }

    private static String doStr(int k) {
        int i = 0;
        String s = "";
        while (i < k) {
            if (randInt(0, 100) % 2 == 0)
                s += (char) randInt(97, 122);
            else
                s += (char) randInt(65, 90);
            i++;
        }
        return s;
    }

    private static List<String> doEx(String s) {
        List<String> rot = rotationsArraySol(s);
        int k = randInt(0, 100);
        if (k % 2 == 0) {
            int i = randInt(0, rot.size() - 1);
            rot.remove(i);
        }
        int n = randInt(0, 5);
        int i = 0;
        while (i < n) {
            rot.add(doStr(randInt(5, 12)));
            i++;
        }
        Collections.shuffle(rot);
        return rot;
    }

    ///
    @Test
    public void test1() {
        System.out.println("Random Tests ****containAllRots");
        for (int i = 0; i < 200; i++) {
            String a = doStr(randInt(8, 15));
            List<String> r = doEx(a);
            testing(Rotations.containAllRots(a, r), containAllRotsSol(a, r));
        }
    }
}
```

### 个人总结：

```
import java.util.List;

public class Rotations {

    public static Boolean containAllRots(String strng, List<String> arr) {
        for (int i = 0; i < strng.length(); i++)
            if (!arr.contains(strng.substring(i, strng.length()) + strng.substring(0, i)))
                return false;
        return true;
    }
}
```

```
import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.IntStream;

public class Rotations {

    public static Boolean containAllRots(String strng, List<String> arr) {
        return arr.containsAll(rotate(strng));
    }

    public static List<String> rotate(String s) {
        return IntStream.range(0, s.length()).mapToObj(i -> s.substring(i, s.length()).concat(s.substring(0, i)))
                .collect(Collectors.toList());
    }

}
```

```
import java.util.List;
import java.util.stream.*;

public class Rotations {
    private static Stream<String> rots(String s) {
        return IntStream.range(0, s.length()).mapToObj(i -> s.substring(i) + s.substring(0, i));
    }

    public static Boolean containAllRots(String strng, List<String> arr) {
        return rots(strng).allMatch(s -> arr.contains(s));
    }
}
```