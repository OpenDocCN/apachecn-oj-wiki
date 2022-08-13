<!--yml
category: codewars
date: 2022-08-13 11:41:29
-->

# Human readable duration format (Codewars 4kyu Python)_AidenLau的博客-CSDN博客

> 来源：[https://blog.csdn.net/AidenLau/article/details/104677723?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-14-104677723-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/AidenLau/article/details/104677723?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-14-104677723-null-null.142^v40^control,185^v2^control&utm_term=codewars)

**题目：**

Your task in order to complete this Kata is to write a function which formats a duration, given as a number of seconds, in a human-friendly way.
The function must accept a non-negative integer. If it is zero, it just returns “now”. Otherwise, the duration is expressed as a combination of years, days, hours, minutes and seconds.
It is much easier to understand with an example:
format_duration(62) # returns “1 minute and 2 seconds”
format_duration(3662) # returns “1 hour, 1 minute and 2 seconds”
For the purpose of this Kata, a year is 365 days and a day is 24 hours.
Note that spaces are important.
Detailed rules
The resulting expression is made of components like 4 seconds, 1 year, etc. In general, a positive integer and one of the valid units of time, separated by a space. The unit of time is used in plural if the integer is greater than 1.
The components are separated by a comma and a space (", "). Except the last component, which is separated by " and ", just like it would be written in English.
A more significant units of time will occur before than a least significant one. Therefore, 1 second and 1 year is not correct, but 1 year and 1 second is.
Different components have different unit of times. So there is not repeated units like in 5 seconds and 1 second.
A component will not appear at all if its value happens to be zero. Hence, 1 minute and 0 seconds is not valid, but it should be just 1 minute.
A unit of time must be used “as much as possible”. It means that the function should not return 61 seconds, but 1 minute and 1 second instead. Formally, the duration specified by of a component must not be greater than any valid more significant unit of time.

**我的思路：**

这题算数字很简单，主要是格式的调整。

单位上如果数字为0，不需要出现；如果数字为1，单位为单数形式；数字大于1，单位为复数形式。

整体格式上，如果有多于一个部分，格式为：{0,3}(XX，) XX and XX；如果只有一个部分，即为：XX。

我构造了两个function，*form()* 和 *readable()*，分别解决这两个问题。

**我的解答：**

```
def format_duration(seconds):
    if seconds == 0:
        return "now"
    y = seconds // (3600*24*365)
    d = (seconds % (3600*24*365))//(3600*24)
    h = (seconds % (3600*24)) // 3600
    m = (seconds % 3600) // 60
    s = seconds % 60
    return readable([form(y,"year"),form(d,"day"),form(h,"hour"),form(m,"minute"),form(s,"second")])

def form(n,unit):
    if n == 0:
        return ""
    if n == 1:
        return "1 "+ unit
    return str(n) + " " + unit + "s"

def readable(l):
    l = list(filter(None, l))
    result = ""
    if len(l) == 1:
        return l[0]
    for i in range(len(l)-1):
        result = result + ", " + l[i]
    result = result + " and " + l[len(l)-1]
    return result[2:] 
```

**Most clever：**

做完题目看一下题后投票clever最多的答案：

```
times = [("year", 365 * 24 * 60 * 60), 
         ("day", 24 * 60 * 60),
         ("hour", 60 * 60),
         ("minute", 60),
         ("second", 1)]

def format_duration(seconds):

    if not seconds:
        return "now"

    chunks = []
    for name, secs in times:
        qty = seconds // secs
        if qty:
            if qty > 1:
                name += "s"
            chunks.append(str(qty) + " " + name)

        seconds = seconds % secs

    return ', '.join(chunks[:-1]) + ' and ' + chunks[-1] if len(chunks) > 1 else chunks[0] 
```

**总结：**

他把数值的计算放在了主循环中，更加方便一点。对单位单复数形式以及整句格式的调整，虽然呈现方式不同，思路一致。我为了自己实现的时候思路清楚一些，把功能拆成了几块分别实现。