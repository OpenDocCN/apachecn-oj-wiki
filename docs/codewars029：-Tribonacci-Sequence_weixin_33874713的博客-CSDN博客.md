<!--yml
category: codewars
date: 2022-08-13 11:46:42
-->

# codewars029: Tribonacci Sequence_weixin_33874713的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_33874713/article/details/92001763?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-92001763.nonecase](https://blog.csdn.net/weixin_33874713/article/details/92001763?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-92001763.nonecase)

[http://www.codewars.com/kata/tribonacci-sequence/train/java](http://www.codewars.com/kata/tribonacci-sequence/train/java)

6 kyu

```
package codewars;
//http://www.codewars.com/kata/tribonacci-sequence/train/java
public class Xbonacci{
  public double[] tribonacci(){
    double[] arr = new double[n];
    if(n == 0){
      return arr;
    }
    int size = n < 3 ? n : 3;
    for(int i = 0; i < size; i++){
      arr[i] = s[i];
    }
    if(n <= 3){
      return arr;
    }
    for(int i = 3; i < n; i++){
      arr[i] = arr[i - 1] + arr[i - 2] + arr[i - 3];
    }
  }
}
```