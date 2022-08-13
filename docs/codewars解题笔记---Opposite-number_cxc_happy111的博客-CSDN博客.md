<!--yml
category: codewars
date: 2022-08-13 11:33:33
-->

# codewars解题笔记---Opposite number_cxc_happy111的博客-CSDN博客

> 来源：[https://blog.csdn.net/cxc_happy111/article/details/86589043?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-86589043.142^v40^control,185^v2^control](https://blog.csdn.net/cxc_happy111/article/details/86589043?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-86589043.142^v40^control,185^v2^control)

**Instructions:**

Very simple, given a number, find its opposite.

Examples:

```
1: -1
14: -14
-34: 34
```

**Sample Tests: **

```
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class OppositeExampleTests {
  @Test
  public void tests() {
    assertEquals(-1, Kata.opposite(1));
  }
}
```

**Solution:**

```
public class Kata
    {
        public static int opposite(int number)
        {
            // your code here
        }
    }
```

**题目的解释：**

很简单，给定一个数字，找到它的相反数。

例如:

1: -1
14: -14
-34: 34

**我的答案：**

```
public class Kata
    {
        public static int opposite(int number)
        {
            number = 0 - number;
            return number;
        }
    }
```

** 最优答案：**

```
public class Kata
    {
        public static int opposite(int number)
        {
            return -number;
        }
    }
```