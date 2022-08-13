<!--yml
category: codewars
date: 2022-08-13 11:46:23
-->

# codewars055: Buying a car_weixin_34390105的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_34390105/article/details/92001797?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-92001797.nonecase](https://blog.csdn.net/weixin_34390105/article/details/92001797?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-92001797.nonecase)

### Instructions

[Buying a car](https://www.codewars.com/kata/554a44516729e4d80b000012/train/java)

### Solution:

```
//https://www.codewars.com/kata/554a44516729e4d80b000012/train/java
import java.math.BigDecimal;
public class BuyCar{
    public static int[] nbMonths(int startPriceOld, int startPriceNew, int savingperMonth, double percentLossByMonth){
        if(startPriceOld >= startPriceNew){
            return new int[]{0, startPriceOld - startPriceNew};
        }    
        int months = 0;
        int left = 0;
        BigDecimal startPriceOld2 = new BigDecimal(String.valueOf(startPriceOld));
        BigDecimal startPriceNew2 = new BigDecimal(String.valueOf(startPriceNew));
        while(true){
            months++;
            if(months > 1 && months % 2 == 1){
                percentLossByMonth += 0.5;                
            }    
            BigDecimal percent = new BigDecimal(String.valueOf(100.0 - percentLossByMonth) / 100);
            startPriceOld2 = startPriceOld2.multiply(percent);
            startPriceNew2 = startPriceNew2.multiply(percent);
            BigDecimal savings = new BigDecimal(String.valueOf(savingperMonth * months));
            BigDeciaml balance = startPriceOld2.add(savings).substract(startPriceNew2);
            if(balance.compareTo(BigDecimal.ZERO) >= 0){
                left = balance.intValue();
                break;
            }    
        }    
        return new int[]{months, left};
    }    
} 
```

### Example Test:

```
TBD 
```