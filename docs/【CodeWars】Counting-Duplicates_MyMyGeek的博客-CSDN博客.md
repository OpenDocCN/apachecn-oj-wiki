<!--yml
category: codewars
date: 2022-08-13 11:42:20
-->

# 【CodeWars】Counting Duplicates_MyMyGeek的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_24342739/article/details/90742927?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-10-90742927-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_24342739/article/details/90742927?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-10-90742927-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## 题意

> 题目链接：[https://www.codewars.com/kata/counting-duplicates/train/java/5cf118cee10216001acc1c83](https://www.codewars.com/kata/counting-duplicates/train/java/5cf118cee10216001acc1c83)

```
Count the number of Duplicates
Write a function that will return the count of distinct case-insensitive alphabetic characters and numeric digits that occur more than once in the input string. The input string can be assumed to contain only alphabets (both uppercase and lowercase) and numeric digits.

Example
"abcde" -> 0 # no characters repeats more than once
"aabbcde" -> 2 # 'a' and 'b'
"aabBcde" -> 2 # 'a' occurs twice and 'b' twice (`b` and `B`)
"indivisibility" -> 1 # 'i' occurs six times
"Indivisibilities" -> 2 # 'i' occurs seven times and 's' occurs twice
"aA11" -> 2 # 'a' and '1'
"ABBA" -> 2 # 'A' and 'B' each occur twice 
```

题目意思很简单，就是求出给定字符串中出现次数最多的字符出现的次数，如果是字母则大小写，思路也比较简单，有人使用Map来记录字符出现的次数去实现，我的做法是定义一个大小为ASCII最大值(127)的数组，以每个字符的ASCII码作为数组的下标，遍历时对数组中的元素进行累加，这个思路虽然有一些空间浪费，但是数组长度127对于计算机来说非常非常小，优点在于代码可以非常简洁，如果用Map来实现还需要检查key是否已经存在、遍历Map需要同时去获取key和value等一些操作，虽然也不复杂，还是更喜欢简洁一些的写法(性能相差不大的情况下)

## 代码

```
public class CountingDuplicates {
    public static int duplicateCount(String text) {
        if (text == null ||text.length() == 0) return 0;

        int result = 0;
        int[] count = new int[127];
        text = text.toUpperCase();
        String[] arr = text.split("");

        for (String s : arr) {
            int index = s.charAt(0);
            count[index]++;
        }

        for (int i : count) {
            if (i > 1) result++;
        }

        return result;
    }
} 
```

测试用例

```
import org.junit.Test;
import static org.junit.Assert.assertEquals;
import org.junit.runners.JUnit4;

public class SolutionTest {
    @Test
    public void abcdeReturnsZero() {
        assertEquals(0, CountingDuplicates.duplicateCount("abcde"));
    }

    @Test
    public void abcdeaReturnsOne() {
        assertEquals(1, CountingDuplicates.duplicateCount("abcdea"));
    }

    @Test
    public void indivisibilityReturnsOne() {
        assertEquals(1, CountingDuplicates.duplicateCount("indivisibility"));
    }

    @Test 
    public void reallyLongStringContainingDuplicatesReturnsThree() {
        String testThousandA = new String(new char[1000]).replace('\0', 'a');
        String testHundredB = new String(new char[100]).replace('\0', 'b');
        String testTenC = new String(new char[10]).replace('\0', 'c');
        String test1CapitalA = new String(new char[1]).replace('\0', 'A'); 
        String test1d = new String(new char[1]).replace('\0', 'd'); 
        String test = test1d + test1CapitalA + testTenC + 
            testHundredB + testThousandA;

        assertEquals(3, CountingDuplicates.duplicateCount(test));
    }

} 
```