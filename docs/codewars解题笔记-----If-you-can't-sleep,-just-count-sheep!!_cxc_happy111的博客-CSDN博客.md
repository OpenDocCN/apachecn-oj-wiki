<!--yml
category: codewars
date: 2022-08-13 11:31:14
-->

# codewars解题笔记-----If you can't sleep, just count sheep!!_cxc_happy111的博客-CSDN博客

> 来源：[https://blog.csdn.net/cxc_happy111/article/details/86538792?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-86538792.142^v40^control,185^v2^control](https://blog.csdn.net/cxc_happy111/article/details/86538792?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-86538792.142^v40^control,185^v2^control)

题的描述：Given a non-negative integer, `3` for example, return a string with a murmur: `"1 sheep...2 sheep...3 sheep..."`. Input will always be valid, i.e. no negative integers.

Sample Tests:

```
import org.junit.Test;
import static org.junit.Assert.assertEquals;
import org.junit.runners.JUnit4;

// TODO: Replace examples and use TDD development by writing your own tests

public class SolutionTest {
    @Test
    public void testSomething() {
        assertEquals("1 sheep...", Kata.countingSheep(1));
        assertEquals("1 sheep...2 sheep...", Kata.countingSheep(2));
        assertEquals("1 sheep...2 sheep...3 sheep...", Kata.countingSheep(3));
    }
}
```

Solution:

```
class Kata {
  public static String countingSheep(int num) {
    //Add your code here
    return "";
  }
}
```

习题的解说：

 题目：如果给定一个非负整数，3例如，返回一个带杂音的字符串：“1只羊…2只羊…3只羊…”。输入将始终有效，即没有负整数。

解释说明：.在Sample Tests:代码中调用了countingSheep（）这个方法，我们要补全这个方法中的代码，并且在Sample Tests:这个里面成立。

我的答案：

```
class Kata {
  public static String countingSheep(int num) {
    StringBuilder sb = new StringBuilder();//定义一个字符串
        for(int i = 1;i<=num;i++){
            sb.append(i + " sheep...");
        }
    return "sb";
  }
}
```