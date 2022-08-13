<!--yml
category: codewars
date: 2022-08-13 11:41:17
-->

# 【Codewars】Valid Braces_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/90315925?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-90315925.142^v40^control,185^v2^control](https://blog.csdn.net/ecysakura/article/details/90315925?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-90315925.142^v40^control,185^v2^control)

### Codewars里的 6kyu Kata。

### 题目说明：

> Write a function that takes a string of braces, and determines if the order of the braces is valid. It should return `true` if the string is valid, and `false` if it's invalid.
> 
> This Kata is similar to the [Valid Parentheses](https://www.codewars.com/kata/valid-parentheses) Kata, but introduces new characters: brackets `[]`, and curly braces `{}`. Thanks to `@arnedag` for the idea!
> 
> All input strings will be nonempty, and will only consist of parentheses, brackets and curly braces: `()[]{}`.
> 
> ### What is considered Valid?
> 
> A string of braces is considered valid if all braces are matched with the correct brace.
> 
> ## Examples
> 
> ```
> "(){}[]"   =>  True
> "([{}])"   =>  True
> "(}"       =>  False
> "[(])"     =>  False
> "[({})](]" =>  False
> ```

堆栈解题，简单。堆栈的大小最好为 n + 1。

### 解题代码：

```
public class BraceChecker {

    public boolean isValid(String braces) {
        // Add code here
        int len = braces.length();
        char[] stack = new char[len + 1];
        int top = 0;
        char ch;
        for (int i = 0; i < len; i++) {
            ch = braces.charAt(i);
            if (ch == '(' || ch == '[' || ch == '{') {
                stack[++top] = ch;
            } else if ((ch == ')' && stack[top] == '(') || (ch == ']' && stack[top] == '[')
                    || (ch == '}' && stack[top] == '{')) {
                top--;
            } else {
                return false;
            }
        }
        if (top != 0)
            return false;
        return true;
    }

}
```

Test Cases:

```
import static org.junit.Assert.*;
import org.junit.Test;

public class BraceCheckerTests {

    private BraceChecker checker = new BraceChecker();

    @Test
    public void testValid() {
        assertEquals(true, checker.isValid("()"));
        assertEquals(true, checker.isValid("[]"));
        assertEquals(true, checker.isValid("{}"));
        assertEquals(true, checker.isValid("(){}[]"));
        assertEquals(true, checker.isValid("([{}])"));
        assertEquals(true, checker.isValid("({})[({})]"));
        assertEquals(true, checker.isValid("(({{[[]]}}))"));
        assertEquals(true, checker.isValid("{}({})[]"));
    }

    @Test
    public void testInvalid() throws Exception {
        assertEquals(false, checker.isValid("[(])"));
        assertEquals(false, checker.isValid("(}"));
        assertEquals(false, checker.isValid("(})"));
        assertEquals(false, checker.isValid(")(}{]["));
        assertEquals(false, checker.isValid("())({}}{()][]["));
        assertEquals(false, checker.isValid("(((({{"));
        assertEquals(false, checker.isValid("}}]]))}])"));
    }

} 
```

### 个人总结：

其他方法：

```
public class BraceChecker {

    public boolean isValid(String braces) {
        String b = braces;
        System.out.println(braces);
        for (int i = 0; i < braces.length() / 2; i++) {
            b = b.replaceAll("\\(\\)", "");
            b = b.replaceAll("\\[\\]", "");
            b = b.replaceAll("\\{\\}", "");
            if (b.length() == 0)
                return true;
        }
        return false;
    }
}

public class BraceChecker {

    public boolean isValid(String s) {
        String lastIteration = s;
        String currentIteration = s;
        do {
            lastIteration = currentIteration;
            currentIteration = lastIteration.replace("[]", "").replace("{}", "").replace("()", "");
        } while (currentIteration.length() < lastIteration.length());
        return currentIteration.equals("");
    }

}

public class BraceChecker {
    public boolean isValid(String s) {
        int x = s.length();
        s = s.replaceAll("\\(\\)|\\[\\]|\\{\\}", "");
        return s.length() == x ? false : s.length() == 0 || isValid(s);
    }
}

import java.util.Map;
import java.util.HashMap;
import java.util.Stack;

public class BraceChecker {

    public boolean isValid(String braces) {
        if (braces == null) {
            return false;
        }

        Stack<Character> stack = new Stack<>();
        Map<Character, Character> map = new HashMap<>();
        map.put(')', '(');
        map.put('}', '{');
        map.put(']', '[');

        for (int i = 0; i < braces.length(); i++) {
            char c = braces.charAt(i);
            if ((c == '(') || (c == '{') || (c == '[')) {
                stack.push(c);
            } else {
                if (stack.empty() || (stack.pop() != map.get(c))) {
                    return false;
                }
            }
        }

        if (stack.empty()) {
            return true;
        }

        return false;
    }

}
```

借鉴，学习。