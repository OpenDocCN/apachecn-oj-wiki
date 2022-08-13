<!--yml
category: codewars
date: 2022-08-13 11:29:14
-->

# CodeWars 关于字符串包含问题_happymff的博客-CSDN博客

> 来源：[https://blog.csdn.net/happymff/article/details/70792320?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-70792320.142^v40^control,185^v2^control](https://blog.csdn.net/happymff/article/details/70792320?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-70792320.142^v40^control,185^v2^control)

Description:

Write function scramble(str1,str2) that returns true if a portion of str1 characters can be rearranged to match str2, otherwise returns false.

For example:
str1 is ‘rkqodlw’ and str2 is ‘world’ the output should return true.
str1 is ‘cedewaraaossoqqyt’ and str2 is ‘codewars’ should return true.
str1 is ‘katas’ and str2 is ‘steak’ should return false.

Only lower case letters will be used (a-z). No punctuation or digits will be included.
Performance needs to be considered

```
public class Scramblies {

    public static boolean scramble(String str1, String str2) {
        if (str2.length() > str1.length()) return false;
        for (String s: str2.split("")) {
          if (!str1.contains(s))  return false;
          str1 = str1.replaceFirst(s,"");
        }        

        return true;
    }
}
```

另一种实现方式

```
import java.util.HashMap;
import java.util.Map;

public class Scramblies {

    public static boolean scramble(String str1, String str2) {
        if (str1.length() < str2.length()) return false;
        Map requirements = new HashMap<>();
        for (char reqChar : str2.toCharArray()) {
            Integer count = requirements.get(reqChar);
            if (count == null) count = 0;
            requirements.put(reqChar, count + 1);
        }

        for (char foundChar : str1.toCharArray()) {
            Integer count = requirements.remove(foundChar);
            if (count == null) continue;
            if (count > 1) requirements.put(foundChar, count - 1);
        }
        return requirements.isEmpty();
    }
}
```