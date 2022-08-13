<!--yml
category: codewars
date: 2022-08-13 11:39:49
-->

# 【Codewars】Shortest Word_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/90315105?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-90315105.142^v40^control,185^v2^control](https://blog.csdn.net/ecysakura/article/details/90315105?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-90315105.142^v40^control,185^v2^control)

### Codewars里的 7kyu Kata。

### 题目说明：

> Simple, given a string of words, return the length of the shortest word(s).
> 
> String will never be empty and you do not need to account for different data types.

使用双指针解题，很简单，但是需要注意结束循环后需要在次进行计算取值。

### 解题代码：

```
import java.util.Arrays;

public class Kata {
    public static int findShort(String s) {
        int i = 0, j = i + 1;
        int res = s.length();
        if(res > 1 && s.charAt(j) == ' ')
            return 1;
        int length = s.length();
        while(j < length){
            if(s.charAt(j) != ' ') {
                j++;
            } else {
                res = res > j - i ? j - i : res;
                i = j + 1;
                j = j + 1;
            }
        }
        res = res > j - i ? j - i : res;
        return res;
    }
}
```

Test Case:

```
import org.junit.Test;

import java.util.Arrays;
import java.util.Random;
import java.util.stream.Collectors;

import static org.junit.Assert.assertEquals;

/**
 * Created by Javatlacati on 01/03/2017.
 */
public class KataTest {
    @Test
    public void findShort() throws Exception {
        assertEquals(3, Kata.findShort("bitcoin take over the world maybe who knows perhaps"));
        assertEquals(3, Kata.findShort("turns out random test cases are easier than writing out basic ones"));

        assertEquals(3, Kata.findShort("lets talk about Java the best language"));
        assertEquals(1, Kata.findShort("i want to travel the world writing code one day"));
        assertEquals(2, Kata.findShort("Lets all go on holiday somewhere very cold"));
    }

    public static int sol(String s) {
        return Arrays.stream(s.split(" ")).mapToInt(c -> c.length()).min().getAsInt();
    }

    String[] names = new String[]{"Bitcoin", "LiteCoin", "Ripple", "Dash", "Lisk", "DarkCoin", "Monero", "Ethereum", "Classic", "Mine", "ProofOfWork", "ProofOfStake", "21inc", "Steem", "Dogecoin", "Waves", "Factom", "MadeSafeCoin", "BTC"};

    @Test
    public void randomTests() throws Exception {
        Random r = new Random();
        int tam = r.nextInt(names.length);
        String a = Arrays.stream(names).unordered().skip(names.length - tam).collect(Collectors.joining(" "));
        assertEquals(sol(a), Kata.findShort(a));
    }
}
```

### 个人总结：

没有考虑循环退出后，漏判了最后一个单词，造成部分错误。