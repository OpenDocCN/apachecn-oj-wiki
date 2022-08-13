<!--yml
category: codewars
date: 2022-08-13 11:49:55
-->

# 【Codewars python 4kyu】: Human readable duration format_小菜鸟快飞的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36362028/article/details/100547613?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-100547613.nonecase](https://blog.csdn.net/qq_36362028/article/details/100547613?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-100547613.nonecase)

# 问题描述：

Your task in order to complete this Kata is to write a function which formats a duration, given as a number of seconds, in a human-friendly way.

The function must accept a non-negative integer. If it is zero, it just returns `"now"`. Otherwise, the duration is expressed as a combination of `years`, `days`, `hours`, `minutes` and `seconds`.

It is much easier to understand with an example:

```
format_duration(62)    # returns "1 minute and 2 seconds"
format_duration(3662)  # returns "1 hour, 1 minute and 2 seconds"
```

**For the purpose of this Kata, a year is 365 days and a day is 24 hours.**

Note that spaces are important.

### Detailed rules

The resulting expression is made of components like `4 seconds`, `1 year`, etc. In general, a positive integer and one of the valid units of time, separated by a space. The unit of time is used in plural if the integer is greater than 1.

The components are separated by a comma and a space (`", "`). Except the last component, which is separated by `" and "`, just like it would be written in English.

A more significant units of time will occur before than a least significant one. Therefore, `1 second and 1 year` is not correct, but `1 year and 1 second` is.

Different components have different unit of times. So there is not repeated units like in `5 seconds and 1 second`.

A component will not appear at all if its value happens to be zero. Hence, `1 minute and 0 seconds` is not valid, but it should be just `1 minute`.

A unit of time must be used "as much as possible". It means that the function should not return `61 seconds`, but `1 minute and 1 second` instead. Formally, the duration specified by of a component must not be greater than any valid more significant unit of time.

# 代码实现：

```
#codewars第十七题 （还未解决）
def format_duration(seconds):
    if seconds == 0: return 'now'
    ss = seconds
    #year
    year = ss // 31536000
    # day
    ss0 = ss - year * 31536000
    day = ss0 // 86400
    #hour
    ss1 = ss0 - day * 86400
    hour = ss1 // 3600
    #min
    ss2 = ss1 - hour * 3600
    minu = ss2 // 60
    #sec
    ss3 = ss2 - minu * 60
    sec = ss3 % 60
    #'year','day','hour','minute','second'
    units = []
    if year == 1: units.append('1 year')   
    if year > 1: 
        units.append(year)
        units.append(' years')
    if day == 1: units.append('1 day')   
    if day > 1: 
        units.append(day)  
        units.append(' days')
    if hour == 1: units.append('1 hour')   
    if hour > 1: 
        units.append(hour) 
        units.append(' hours')
    if minu == 1: units.append('1 minute')   
    if minu > 1: 
        units.append(minu) 
        units.append(' minutes')
    if sec == 1: units.append('1 second')   
    if sec > 1:
        units.append(sec ) 
        units.append(' seconds')
    print(year)
    print(day)
    print(hour)
    print(minu)
    print(sec)
    print(units)
    _length = len(units)

        times = [("year", 365 * 24 * 60 * 60), 
         ("day", 24 * 60 * 60),
         ("hour", 60 * 60),
         ("minute", 60),
         ("second", 1)]

#另解一
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

#另解二
def format_duration(seconds):
    if seconds == 0: return "now"
    origin = seconds
    dic = {
        'year': 60 * 60 * 24 * 365,
        'day': 60 * 60 * 24,
        'hour': 60 * 60,
        'minute': 60,
        'second': 1
    }
    spent = {}
    ans = ""
    for x in ['year','day','hour','minute','second']:
        spent[x] = seconds // dic[x]
        ans += "{}{} {}{}".format('' if seconds == origin else ' and ' if seconds % dic[x] == 0 else ', ', spent[x], x,'s' if spent[x] > 1 else '') if spent[x] > 0 else '' 
        seconds %= dic[x]
    return  ans

format_duration(3662)
```