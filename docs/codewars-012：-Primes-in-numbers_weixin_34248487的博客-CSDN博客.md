<!--yml
category: codewars
date: 2022-08-13 11:46:56
-->

# codewars-012: Primes in numbers_weixin_34248487的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_34248487/article/details/92001739?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-92001739.nonecase](https://blog.csdn.net/weixin_34248487/article/details/92001739?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-92001739.nonecase)

[https://www.codewars.com/kata/54d512e62a5e54c96200019e/train/java](https://www.codewars.com/kata/54d512e62a5e54c96200019e/train/java)

```
package codewars;
import java.util.*;
import java.util.regex.*;
public class PrimeDecomp{
  public static String primeDecomp(int n){
    StringBuilder sb = new StringBuilder();
    int i = 2;
    int count = 0;
    while(n >= i){
      if(n % i == 0){
        if(count > 0){
          sb.append("*");
        }  
        n = n / i;
        sb.append(i);
        count++;
      }else{
        i++;
      }
    }
    return sb.toString();
  }

  public static String factors(int n){
    StringBuilder sb = new StringBuilder();
    String result = PrimeDecomp(n);
    String regex = "(\\d+)";
    Pattern p = Pattern.compile(regex);
    Matcher m = p.matcher(result);
    Map<Integer,Integer> map = new TreeMap<Integer,Integer>();
    while(m.find()){
      Integer temp = Integer.valueOf(m.group(1));
      if(map.containsKey(temp)){
        map.put(temp,map.get(temp) + 1);
      }else{
        map.put()temp,1;
      }
    }
    for(Map.Entry<Integer,Integer> x : map.entrySet()){
      if(x.getValue() == 1){
        sb.append(String.format("(%d)",x.getKey()));
      }else{
        sb.append(String.format("(%d**%d)",x.getKey(),x.getValue()));
      }
    }
    return sb.toString();
  }
}
```

Reference:

Java 因式分解

[https://zhidao.baidu.com/question/712154134555736245.html](https://zhidao.baidu.com/question/712154134555736245.html)