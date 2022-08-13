<!--yml
category: codewars
date: 2022-08-13 11:49:44
-->

# codewars??? Is my friend cheating?_weixin_33758863的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_33758863/article/details/92001755?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-92001755.nonecase](https://blog.csdn.net/weixin_33758863/article/details/92001755?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-92001755.nonecase)

[https://www.codewars.com/kata/5547cc7dcad755e480000004/train/java](https://www.codewars.com/kata/5547cc7dcad755e480000004/train/java)

```
import java.util.*;
public class RemovedNumbers{
  public static List<long[]> removNb(long n){
    List<long[]> arr = new ArrayList<long[]>();
    long sum = (1+n) * n /2;
    for(long i=n/2+1; i<=n; i++){
      for(long j=n/2+2; j<=n; j++){
        long product = i * j;
        long left = sum - i - j;
        if(i != j){
          if(product == left){
            arr.add(new long[]{i,j});
            arr.add(new long[]{j,i});
            //return arr;
          }
          if(product > left){
            break;
          }
        }
      }
    }
    return arr;
  }
}
```

Process was terminated. It took longer than 12000ms to complete