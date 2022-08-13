<!--yml
category: codewars
date: 2022-08-13 11:49:58
-->

# 【CodeWars】Human readable duration format_MyMyGeek的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_24342739/article/details/90609356?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-90609356.nonecase](https://blog.csdn.net/qq_24342739/article/details/90609356?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-90609356.nonecase)

## 1.题意

> 题目链接：[https://www.codewars.com/kata/52742f58faf5485cae000b9a](https://www.codewars.com/kata/52742f58faf5485cae000b9a)

```
Your task in order to complete this Kata is to write a function which formats a duration, given as a number of seconds, in a human-friendly way.

The function must accept a non-negative integer. If it is zero, it just returns "now". Otherwise, the duration is expressed as a combination of years, days, hours, minutes and seconds.

It is much easier to understand with an example:

TimeFormatter.formatDuration(62)   //returns "1 minute and 2 seconds"
TimeFormatter.formatDuration(3662) //returns "1 hour, 1 minute and 2 seconds"
For the purpose of this Kata, a year is 365 days and a day is 24 hours.

Note that spaces are important.

Detailed rules
The resulting expression is made of components like 4 seconds, 1 year, etc. In general, a positive integer and one of the valid units of time, separated by a space. The unit of time is used in plural if the integer is greater than 1.

The components are separated by a comma and a space (", "). Except the last component, which is separated by " and ", just like it would be written in English.

A more significant units of time will occur before than a least significant one. Therefore, 1 second and 1 year is not correct, but 1 year and 1 second is.

Different components have different unit of times. So there is not repeated units like in 5 seconds and 1 second.

A component will not appear at all if its value happens to be zero. Hence, 1 minute and 0 seconds is not valid, but it should be just 1 minute.

A unit of time must be used "as much as possible". It means that the function should not return 61 seconds, but 1 minute and 1 second instead. Formally, the duration specified by of a component must not be greater than any valid more significant unit of time. 
```

题目意思很简单，就是给定一个秒数seconds，计算这个seconds的year、day、hour、minute、second，以"1year, 2 days, 1 hour, 1 minute and 2 seconds"这样形式的字符串返回，其中数值为0 的部分不显示，最后一个数值用"and"拼接，如果这个0秒则返回"now"

## 2.代码

一开始想的是算出这些值，然后用if else来进行判断拼接字符串，后来发现需要嵌套的if else太多了，就改为使用一个队列，计算过程中把这些数值对应的字符串按year、day、hour、minute、second的顺序加入到队列中，全部计算完成之后一个一个出队拼接到最终需要返回的字符串中，通过队列的大小来判断当前使用逗号拼接还是用"and"拼接

```
import java.util.LinkedList;
import java.util.Queue;

public class TimeFormatter {  
    public static String formatDuration(int seconds) {

        if (seconds == 0) return "now";

        int oneMinute = 60;
        int oneHour = 60 * oneMinute;
        int oneDay = 24 * oneHour;
        int oneYear = 365 * oneDay;

        Queue<String> queue = new LinkedList<>();

        String result = "";
        int year = seconds / oneYear;
        if (year == 1) queue.add(year + " year"); else if (year > 1) queue.add(year + " years");
        seconds = seconds - year * oneYear;

        int day =  seconds / oneDay;
        if (day == 1) queue.add(day + " day"); else if (day > 1) queue.add(day + " days");
        seconds = seconds - day * oneDay;

        int hour = seconds / oneHour;
        if (hour == 1) queue.add(hour + " hour"); else if (hour > 1) queue.add(hour + " hours");
        seconds = seconds - hour * oneHour;

        int minute = seconds / oneMinute;
        if (minute == 1) queue.add(minute + " minute"); else if (minute > 1) queue.add(minute + " minutes");
        seconds = seconds - minute * oneMinute;

        if (seconds == 1) queue.add(seconds + " second"); else if (seconds > 1) queue.add(seconds + " seconds");

        StringBuilder stringBuilder = new StringBuilder();

        while (!queue.isEmpty()){
            String tmp = queue.poll();
            stringBuilder.append(tmp);
            if (queue.size() > 1){
                stringBuilder.append(", ");
            }else if (queue.size() == 1){
                stringBuilder.append(" and ");
            }
        }

        return stringBuilder.toString();
    }
} 
```

测试用例

```
import org.junit.Test;
import static org.junit.Assert.*;

public class TimeFormatterTest {
    @Test
    public void testFormatDurationExamples() {

        assertEquals("1 second", TimeFormatter.formatDuration(1));
        assertEquals("1 minute and 2 seconds", TimeFormatter.formatDuration(62));
        assertEquals("2 minutes", TimeFormatter.formatDuration(120));
        assertEquals("1 hour", TimeFormatter.formatDuration(3600));
        assertEquals("1 hour, 1 minute and 2 seconds", TimeFormatter.formatDuration(3662));
        assertEquals("1 hour and 1 second", TimeFormatter.formatDuration(3601));
    }
} 
```

> 另外，有人给出了一种很简洁的Python写法，使用了if else表达式，具体可以参考[https://segmentfault.com/a/1190000006704096](https://segmentfault.com/a/1190000006704096)