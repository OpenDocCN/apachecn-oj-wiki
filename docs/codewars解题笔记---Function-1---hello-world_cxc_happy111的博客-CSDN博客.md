<!--yml
category: codewars
date: 2022-08-13 11:36:33
-->

# codewars解题笔记---Function 1 - hello world_cxc_happy111的博客-CSDN博客

> 来源：[https://blog.csdn.net/cxc_happy111/article/details/86604205?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-86604205.142^v40^control,185^v2^control](https://blog.csdn.net/cxc_happy111/article/details/86604205?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-86604205.142^v40^control,185^v2^control)

### Description:

Make a simple function called **greet** that returns the most-famous "hello world!".

**Test Driven Development (TDD)**

```
import org.junit.Test;
import static org.junit.Assert.assertEquals;
import org.junit.runners.JUnit4;

// TODO: Replace examples and use TDD development by writing your own tests

public class SolutionTest {
    @Test
    public void testSomething() {
        // assertEquals("expected", "actual");
    }
}
```

**Solution:**

```
public class HelloWorld {
  public static String greet() {
    //Make it say "hello world!"
  }
}
```

**题目解说：**

描述：

创建一个名为greet的简单函数，返回最著名的“hello world！”.

我的答案：

```
public class HelloWorld {
  public static String greet() {
    //Make it say "hello world!"
     return "hello world!";
  }
}
```