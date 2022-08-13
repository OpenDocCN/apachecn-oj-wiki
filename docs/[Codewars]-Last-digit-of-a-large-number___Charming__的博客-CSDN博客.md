<!--yml
category: codewars
date: 2022-08-13 11:46:12
-->

# [Codewars]-Last digit of a large number___Charming__的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41882147/article/details/81029486?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-81029486.nonecase](https://blog.csdn.net/qq_41882147/article/details/81029486?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-81029486.nonecase)

### 大数字的最后一位数字（Last digit of a large number） ——大数取模

#### 题目：

*   题目很简单，给出`a,b`两个数字，计算 ab a b 的最后一位数字。
*   例如：`a=2,b=4`， ab=24=16 a b = 2 4 = 16 ，故16的最后一位数字应该是6

#### 思路：

*   对于小数，直接计算然后取模（%10）就可以了
*   但是对于大数，往往就会计算不出来或者十分费时。
*   想了很久，做了很多尝试方案，发现都是时间爆栈了。。
*   后来百度了下才发现这个叫**快速幂取模**。。。可怜楼主没有ACM经验，数学数论也不行。。。
*   那我们直接根据快速幂取模的方法计算就可以了。

#### 讲解快速幂取模：

首先有如下公式：

a∗b%m=[(a%m)∗(b%m)]%m a ∗ b % m = [ ( a % m ) ∗ ( b % m ) ] % m

其证明过程如下：

 a=a1∗m+a2b=b1∗m+b2则a∗b%m=a2∗b2%m=[(a%m)∗(b%m)]%m a = a 1 ∗ m + a 2 b = b 1 ∗ m + b 2 则 a ∗ b % m = a 2 ∗ b 2 % m = [ ( a % m ) ∗ ( b % m ) ] % m

因此

ab%m a b % m

有如下公式:

 ab%m=[(a%m)b]%m=[(a%m)∗(a%m)b−1]%m={(a%m)∗[(a%m)b−1%m]}%m a b % m = [ ( a % m ) b ] % m = [ ( a % m ) ∗ ( a % m ) b − 1 ] % m = { ( a % m ) ∗ [ ( a % m ) b − 1 % m ] } % m

不过根据上面公式，如果b足够大的时候，计算的耗时依旧非常大。

于是可以用下面这种方法：
快速幂算法+可迅速求出 ab a b 。其主要的理论依据如下：
1\. 当b是偶数时， ab a b 可以转化为 a2 a 2 的 b/2 b / 2 次方。
2\. 当b是奇数时， ab a b 可以转化为 a2 a 2 的 b/2 b / 2 次方，再乘以 a a

利用快速幂方法，可以迅速求出一个数的任意次方，再结合**<nobr aria-hidden="true">ab%m={(a%m)∗[(a%m)b−1%m]}%m</nobr><math xmlns="http://www.w3.org/1998/Math/MathML"><msup><mi>a</mi><mi>b</mi></msup><mi mathvariant="normal">%</mi><mi>m</mi><mo>=</mo><mo fence="false" stretchy="false">{</mo><mo stretchy="false">(</mo><mi>a</mi><mi mathvariant="normal">%</mi><mi>m</mi><mo stretchy="false">)</mo><mo>∗</mo><mo stretchy="false">[</mo><mo stretchy="false">(</mo><mi>a</mi><mi mathvariant="normal">%</mi><mi>m</mi><msup><mo stretchy="false">)</mo><mrow class="MJX-TeXAtom-ORD"><mi>b</mi><mo>−</mo><mn>1</mn></mrow></msup><mi mathvariant="normal">%</mi><mi>m</mi><mo stretchy="false">]</mo><mo fence="false" stretchy="false">}</mo><mi mathvariant="normal">%</mi><mi>m</mi></math>公式，就可以得到下面代码：**

#### 解答：

(python 2.7)

```
def last_digit(a, b):
    sum = 1
    a = a%10
    while b>0 :
        if b%2 == 1:
            sum = sum * a % 10
        b /= 2
        a = a * a % 10
    return sum
```

#### 后记：

一开始我坚持用js写的。后来发现`3715290469715693021198967285016729344580685479654510946723`这个数字，在js里会变成科学计数法:`3.715290469715693e+57`,而且 3715290469715693021198967285016729344580685479654510946723%10=8 3715290469715693021198967285016729344580685479654510946723 % 10 = 8 ，这明显不对嘛。。。于是放弃转战python，顺利实现

提交之后看见大神的答案，发现自己还是太年轻了

```
def last_digit(n1, n2):
    return pow( n1, n2, 10 )
```

而且能够通过测试

果然python处理数据也是很强大的

### 参考文献：

1.  [快速幂—java_c_android](https://blog.csdn.net/java_c_android/article/details/55802041)
2.  [快速幂与快速取模—flqbestboy](https://blog.csdn.net/flqbestboy/article/details/8186927)
3.  [ACM算法：快速幂取模（详细）—陌梦路](https://blog.csdn.net/dbc_121/article/details/77646508)