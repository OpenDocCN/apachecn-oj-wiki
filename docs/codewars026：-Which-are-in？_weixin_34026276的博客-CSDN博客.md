<!--yml
category: codewars
date: 2022-08-13 11:47:03
-->

# codewars026: Which are in?_weixin_34026276的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_34026276/article/details/92001760?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-92001760.nonecase](https://blog.csdn.net/weixin_34026276/article/details/92001760?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-92001760.nonecase)

[https://www.codewars.com/kata/550554fd08b86f84fe000a58/train/java](https://www.codewars.com/kata/550554fd08b86f84fe000a58/train/java)

```
package codewars;
//--https://www.codewars.com/kata/550554fd08b86f84fe000a58/train/java
import java.util.*;
public class WhichAreIn{
  private static Boolean isSubstring(String str, String[] arr){
    for(String x : arr){
      if(x.contains(str)){
        return true;
      }
    }
    return false;
  }
  public static String[] inArray(String[] array1, String[] array2){
    Arrays.sort(array1);
    List<String> list = new ArrayList<String>();
    for(String x : array1){
      if(WhichAreIn.isSubstring(x, array2)){
        list.add(x);
      }
    }
    return list.toArray(new String[0]);
  }
}
```