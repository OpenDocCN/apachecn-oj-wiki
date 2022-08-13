<!--yml
category: codewars
date: 2022-08-13 11:44:38
-->

# CodeWars之C#0007_那个妹子留步的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41995872/article/details/86611339?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-86611339.nonecase](https://blog.csdn.net/weixin_41995872/article/details/86611339?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-86611339.nonecase)

输入是总秒数，一年按365天计算，一天按24小时计算

 // formatDuration(62)    // returns "1 minute and 2 seconds"
    //formatDuration(3662)  // returns "1 hour, 1 minute and 2 seconds"

  //formatDuration(0)  // returns "Now"

```
 string Get(int seconds)
    {
        int year = seconds / 31536000;//得到年        
        int day = (seconds - 31536000 * year) / 86400;//减去完整的年的倍数 得到天
        int hour = (seconds - 31536000 * year - 86400 * day) / 3600;//总时间-年数-天数 
        int minute = (seconds - 31536000 * year - 86400 * day - 3600 * hour) / 60;
        int second = seconds - 31536000 * year - 86400 * day - 3600 * hour - 60 * minute;
        Debug.Log(string.Format("总时间： year:{0}   day:{1}   hour:{2}  minute:{3}   second:{4}", year, day, hour, minute, second));
        string result = "";
        if (second>=1)
        {
            result = second == 1 ? ("1 second") : (second.ToString() + " seconds");
        }
        if (minute>=1)
        {
            if (result=="")
            {
                result = minute == 1 ? ("1 minute") : (minute.ToString() + " minutes");
            }
            else
            {
                result = (minute == 1 ? ("1 minute") : (minute.ToString() + " minutes"))+" and " + result;
            }
        }
        if (hour>=1)
        {
            if (result == "")
            {
                result = hour == 1 ? ("1 hour") : (hour.ToString() + " hours");
            }
            else
            {
                if (result.Contains("and"))
                {
                    result = (hour == 1 ? ("1 hour") : (hour.ToString() + " hours")) + ", " + result;
                }
                else
                {
                    result = (hour == 1 ? ("1 hour") : (hour.ToString() + " hours")) + " and " + result;
                }

            }
        }
        if (day >= 1)
        {
            if (result == "")
            {
                result = day == 1 ? ("1 day") : (day.ToString() + " days");
            }
            else
            {
                if (result.Contains("and"))
                {
                    result = (day == 1 ? ("1 day") : (day.ToString() + " days")) + ", " + result;
                }
                else
                {
                    result = (day == 1 ? ("1 day") : (day.ToString() + " days")) + " and " + result;
                }

            }
        }
        if (year >= 1)
        {
            if (result == "")
            {
                result = year == 1 ? ("1 year") : (year.ToString() + " years");
            }
            else
            {
                if (result.Contains("and"))
                {
                    result = (year == 1 ? ("1 year") : (year.ToString() + " years")) + ", " + result;
                }
                else
                {
                    result = (year == 1 ? ("1 year") : (year.ToString() + " years")) + " and " + result;
                }
            }
        }
        if (result=="")
        {
            result = "now";
        }
        return result;

    }

    //1分钟60s  1小时3600s   一天86400s   一年31536000
    //，一年是365天，一天是24小时。
```