<!--yml
category: codewars
date: 2022-08-13 11:51:54
-->

# Codewars解题Are they the "same"?_kaisens的博客-CSDN博客

> 来源：[https://blog.csdn.net/kaisens/article/details/78816643?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-78816643.nonecase](https://blog.csdn.net/kaisens/article/details/78816643?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-78816643.nonecase)

> **题目**
> Given two arrays a and b write a function comp(a, b) (compSame(a, b)
> in Clojure) that checks whether the two arrays have the “same”
> elements, with the same multiplicities. “Same” means, here, that the
> elements in b are the elements in a squared, regardless of the order.
> 
> Examples
> 
> Valid arrays
> 
> a = [121, 144, 19, 161, 19, 144, 19, 11] b = [121, 14641, 20736,
> 361, 25921, 361, 20736, 361] comp(a, b) returns true because in b 121
> is the square of 11, 14641 is the square of 121, 20736 the square of
> 144, 361 the square of 19, 25921 the square of 161, and so on. It gets
> obvious if we write b’s elements in terms of squares:

**谷歌翻译**:

> 给定两个数组a并b写一个函数comp(a, b)（compSame(a,
> b)在Clojure中），检查两个数组是否具有相同的元素，具有相同的多重性。在这里，“相同”是指无论顺序如何，其中的元素b都是a平方的元素。
> 
> 例子
> 
> 有效的数组
> 
> a = [121, 144, 19, 161, 19, 144, 19, 11] b = [121, 14641, 20736,
> 361, 25921, 361, 20736, 361] comp(a,
> b)因为b121是11的平方，14641是121的平方，144是平方，361是19的平方，25921是161的平方，依此类推。如果我们b按照正方形编写元素，这是显而易见的：
> 
> a = [121, 144, 19, 161, 19, 144, 19, 11] b = [11*11, 121*121,
> 144*144, 19*19, 161*161, 19*19, 144*144, 19*19] 无效的数组
> 
> 如果我们把第一个数字改成其他的数字，comp可能不会再变成真的了：
> 
> a = [121, 144, 19, 161, 19, 144, 19, 11] b = [132, 14641, 20736,
> 361, 25921, 361, 20736, 361] comp(a,b)返回假，因为在b132不是任何数量的平方a。
> 
> a = [121, 144, 19, 161, 19, 144, 19, 11] b = [121, 14641, 20736,
> 36100, 25921, 361, 20736, 361] comp(a,b)返回false，因为在b36100中不是任何数量的平方a。
> 
> 备注
> 
> a或者b可能是[]（R，Shell以外的所有语言）。 a或者b可能是nil或null或None（除了在Haskell，酏剂，C
> ++，锈病，R，壳牌）。
> 
> 如果a或b有nil（或null或None），这个问题就没有意义了那么返回false。
> 
> 如果a或者b是空的，结果本身就是明显的。
> 
> C的注意事项
> 
> 这两个数组的大小(> 0)与函数中的参数大小相同comp。

大意就是如果数组b中的数据与数组a中的数据的平方一一对应则返回true 反之返回false

以下为我的代码

```
public class AreSame {

    public static boolean comp(int[] a, int[] b) {

    if(a==null||b==null){
        return false;
    }

    int sum1 = 0;

    int sum2 = 0;

    for(int j = 0;j<b.length;j++){
      sum2+=b[j];
    }

    for(int i = 0 ;i<a.length;i++){

      int tem =  0 ;

      int aa = a[i]*a[i];

      sum1+=aa;
      for(int j = 0;j<b.length;j++){

        if(aa==b[j]){

          if(tem==0){

            tem++;

            b[j]=b[j]+1;
          }
        }
      }

      if(tem==0){
        return false;
      }
    }

    if(sum1!=sum2){
      return false;
    }

    return true;
  }
}
```

该方法已经通过校验

以下代码为评分较高的解决方案
stream为jdk1.8中的方法

```
import java.util.Arrays;

public class AreSame {
  public static boolean comp(final int[] a, final int[] b) {
    return a != null && b != null && a.length == b.length && Arrays.equals(Arrays.stream(a).map(i -> i * i).sorted().toArray(), Arrays.stream(b).sorted().toArray());
  }
}
```

说实话我看不懂