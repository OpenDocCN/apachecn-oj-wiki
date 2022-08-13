<!--yml
category: codewars
date: 2022-08-13 11:46:10
-->

# codewars解题笔记---Grasshopper - Summation_cxc_happy111的博客-CSDN博客

> 来源：[https://blog.csdn.net/cxc_happy111/article/details/86604092?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-86604092.nonecase](https://blog.csdn.net/cxc_happy111/article/details/86604092?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-86604092.nonecase)

### **Instructions:**

**Summation:**

Write a program that finds the summation of every number from 1 to num. The number will always be a positive integer greater than 0.

**For example:**

```
summation(2) -> 3
1 + 2

summation(8) -> 36
1 + 2 + 3 + 4 + 5 + 6 + 7 + 8
```

**Sample Tests:**

```
import java.util.Random;
import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class GrassHopperTest {
    @Test
    public void test1() {
        assertEquals(1,
        GrassHopper.summation(1));
    }
    @Test
    public void test2() {
        assertEquals(36,
        GrassHopper.summation(8));
    }
}
```

** Solution:**

```
public class GrassHopper {

    public static int summation(int n) {

        return 0;
    }
}
```

**题目解说：**

编写一个程序，查找从1到num的每个数字的总和。该数字始终是大于0的正整数。

例如：

```
summation(2) -> 3
1 + 2

summation(8) -> 36
1 + 2 + 3 + 4 + 5 + 6 + 7 + 8
```

**我的答案：**

```
public class GrassHopper {

    public static int summation(int n) {
        int sum;
        int sum2 = 0;
        for(int i = 1;i<=n;i++){
            sum = i;
            sum2 = sum + sum2;
        }
        return sum2;
    }
}
```

**最优答案：**

```
public class GrassHopper {

    public static int summation(int n) {

        return  n*(n+1)/2;
    }
}
```