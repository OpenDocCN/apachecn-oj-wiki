<!--yml
category: codewars
date: 2022-08-13 11:28:48
-->

# codewars解题笔记---The Feast of Many Beasts_cxc_happy111的博客-CSDN博客

> 来源：[https://blog.csdn.net/cxc_happy111/article/details/86609040?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-86609040.142^v40^control,185^v2^control](https://blog.csdn.net/cxc_happy111/article/details/86609040?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-86609040.142^v40^control,185^v2^control)

**Instructions：**

All of the animals are having a feast! Each animal is bringing one dish. There is just one rule: the dish must start and end with the same letters as the animal's name. For example, the great blue heron is bringing garlic naan and the chickadee is bringing chocolate cake.

Write a function `feast` that takes the animal's name and dish as arguments and returns true or false to indicate whether the beast is allowed to bring the dish to the feast.

Assume that `beast` and `dish` are always lowercase strings, and that each has at least two letters. `beast` and `dish` may contain hyphens and spaces, but these will not appear at the beginning or end of the string. They will not contain numerals.

**Sample Tests:**

```
import org.junit.Test;
import static org.junit.Assert.*;
import org.junit.runners.JUnit4;

// TODO: Replace examples and use TDD development by writing your own tests

public class SolutionTest {
    @Test
    public void fixedTest() {
         assertTrue(Kata.feast("great blue heron","garlic nann"));
         assertTrue(Kata.feast("chickadee","chocolate cake"));
         assertFalse(Kata.feast("brown bear","bear claw"));
    }
}
```

**Solution:**

```
public class Kata {

  public static boolean feast(String beast, String dish) {

    return false;

  }
} 
```

**题目的解释：**

所有的动物都在享用盛宴！每只动物都带来一道菜。只有一条规则：菜的开头和结尾必须与动物的名字相同。例如，大蓝鹭带来了大蒜，而山雀带来了巧克力蛋糕。
写一个函数盛宴，以动物的名字和盘子作为论据，返回“真”或“假”，表明是否允许野兽把盘子带到盛宴上。
假设beast和dish总是小写字符串，并且每个字符串至少有两个字母。Beast和Dish可能包含连字符和空格，但这些不会出现在字符串的开头或结尾。它们不包含数字。（俗话就是两个字符串的首尾的字母一致的话就返回true）

**我的答案：**

```
public class Kata {

  public static boolean feast(String beast, String dish) {
       String shou = beast.substring(0,1);
       String shou2 = dish.substring(0,1);
       String wei = beast.substring(beast.length()-1,beast.length());
       String wei2 = dish.substring(dish.length()-1,dish.length());
       if(shou.equals(shou2) && wei.equals(wei2)){
           return true;
       }else{
           return false;
       }
  }
}
```

**最优答案：**

```
public class Kata {

  public static boolean feast(String beast, String dish) {

    return beast.charAt(0)==dish.charAt(0) && beast.charAt(beast.length()-1) == dish.charAt(dish.length()-1);

  }

}
```