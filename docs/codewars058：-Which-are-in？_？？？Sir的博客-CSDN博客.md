<!--yml
category: codewars
date: 2022-08-13 11:46:49
-->

# codewars058: Which are in?_???Sir的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_34268169/article/details/92001815?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-92001815.nonecase](https://blog.csdn.net/weixin_34268169/article/details/92001815?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-92001815.nonecase)

### Instructions:

[Link](https://www.codewars.com/kata/550554fd08b86f84fe000a58/train/java)

### Solution:

```
import java.util.*;
public class WhichAreIn{
    public static String[] inArray(String[] array1, String[] array2){
        List<String> list = new ArrayList<String>();
        for(int i = 0; i < array1.length; i++){
            for(int j = 0; j < array2.length; j++){
                if(!list.contains(array1[i])){
                    list.add(array1[i]);
                    break;
                }    
            }    
        }    
        String[] rslt = list.toArray(new String[0]);
        Arrays.sort(rslt);
        return rslt;
    }    
} 
```

### Example Tests:

```
//https://www.codewars.com/kata/550554fd08b86f84fe000a58/train/java 
```