<!--yml
category: codewars
date: 2022-08-13 11:46:27
-->

# codewars056: Common Denominators 公分母_weixin_34383618的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_34383618/article/details/92001802?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-92001802.nonecase](https://blog.csdn.net/weixin_34383618/article/details/92001802?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-92001802.nonecase)

### Instructions:

[Common Denominators](https://www.codewars.com/kata/54d7660d2daf68c619000d95/train/java)

### Solution:

```
public class Fracts{
    private static long maximumCommonDivisor(long m, long n){
        while(m % n != 0){
            long temp = m % n;
            m = n;
            n = temp;
        }    
        return n;
    }    
    private static long leastCommonMultiple(long m, long n){
        return m * n / Fracts.maximumCommonDivisor(m,n);
    }    
    public static String convertFrac(long[][] lst){
          long mul = Fracts.leastCommonMultiple(lst[0][1],lst[1][1]);  
          for(int i = 2; i < lst.length; i++){
            mul = Fracts.leastCommonMultiple(mul, lst[i][1]);
          }  
        StringBuilder sb = new StringBuilder();
        for(int i = 0; i < lst.length; i++){
            sb.append(String.format("(%d,%d)",mul*lst[i][0]/lst[i][1],mul),);
        }   
        return sb.toString(); 
    }    
} 
```

### Example Tests:

```
TBD
https://www.codewars.com/kata/54d7660d2daf68c619000d95/train/java 
```