<!--yml
category: codewars
date: 2022-08-13 11:46:14
-->

# codewars解题笔记---L1: Set Alarm_cxc_happy111的博客-CSDN博客

> 来源：[https://blog.csdn.net/cxc_happy111/article/details/86609217?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-86609217.nonecase](https://blog.csdn.net/cxc_happy111/article/details/86609217?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-86609217.nonecase)

**Instructions：**

Write a function named setAlarm which receives two parameters. The first parameter, *employed*, is true whenever you are employed and the second parameter, *vacation* is true whenever you are on vacation.

The function should return true if you are employed and not on vacation (because these are the circumstances under which you need to set an alarm). It should return false otherwise. Examples:

```
setAlarm(true, true) -> false
setAlarm(false, true) -> false
setAlarm(false, false) -> false
setAlarm(true, false) -> true
```

**Sample Tests:**

```
import static org.junit.Assert.*;
import org.junit.Test;

public class AlarmTest {

	@Test
	public void setAlarmTest() {
		assertTrue("Should be true.", Alarm.setAlarm(true, false));
		assertFalse("Should be false.", Alarm.setAlarm(true, true));
		assertFalse("Should be false.", Alarm.setAlarm(false, false));
		assertFalse("Should be false.", Alarm.setAlarm(false, true));
	}

}
```

** Solution:**

```
public class Alarm {

  public static boolean setAlarm(boolean employed, boolean vacation) {
    // Your code here...
  }

}
```

**题目解说：**

编写一个名为setalarm的函数，它接收两个参数。第一个参数employed在受雇时为true，第二个参数vaision在休假时为true。

如果您受雇而不是休假，则该功能应返回“真”（因为您需要在这些情况下设置警报）。否则应该返回false。实例：

setAlarm(true, true) -> false
setAlarm(false, true) -> false
setAlarm(false, false) -> false
setAlarm(true, false) -> true

**我的答案：**

```
public class Alarm {

  public static boolean setAlarm(boolean employed, boolean vacation) {
    // Your code here...
        if(employed == true && vacation==true){
            return false;
        }else if(employed == false && vacation == false){
            return false;
        }else if(employed == false && vacation == true){
            return false;
        }else {
            return true;
        }
    }
}
```

**最优答案：**

```
public class Alarm {

  public static boolean setAlarm(boolean employed, boolean vacation) {
    return employed && !vacation;
  }

}
```