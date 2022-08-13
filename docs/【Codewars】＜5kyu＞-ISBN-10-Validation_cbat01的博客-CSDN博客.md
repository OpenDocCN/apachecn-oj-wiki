<!--yml
category: codewars
date: 2022-08-13 11:39:47
-->

# 【Codewars】＜5kyu＞ ISBN-10 Validation_cbat01的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_36270908/article/details/111478820?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-111478820.142^v40^control,185^v2^control](https://blog.csdn.net/weixin_36270908/article/details/111478820?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-111478820.142^v40^control,185^v2^control)

## 一、题目：

> ISBN-10 identifiers are ten digits long. The first nine characters are digits 0-9\. The last digit can be 0-9 or X, to indicate a value of 10.
> An ISBN-10 number is valid if the sum of the digits multiplied by their position modulo 11 equals zero.
> 
> **这道题的目的是让我们去判断一串字符串是不是ISBN码，这道题目的核对标准如下（最新国际标准书号与此题不一致，可以[点击查看](https://baike.baidu.com/item/%E5%9B%BD%E9%99%85%E6%A0%87%E5%87%86%E4%B9%A6%E5%8F%B7/3271472?fr=aladdin)）：将一串字符串的前10位数依序分别乘以从1到10的数目，将其乘积相加，总和用11去除，若余数是0，则该数是ISBN**
> （注：前9个字符是数字0-9。最后一个数字可以是0-9或X，X表示值为10。）

```
例如:
ISBN     : 1 1 1 2 2 2 3 3 3  9
位置      : 1 2 3 4 5 6 7 8 9 10

这是一个有效的ISBN，因为：

(1*1 + 1*2 + 1*3 + 2*4 + 2*5 + 2*6 + 3*7 + 3*8 + 3*9 + 9*10) % 11 = 0 
```

### 二、例子

```
1112223339   -->  true
111222333    -->  false
1112223339X  -->  false
1234554321   -->  true
1234512345   -->  false
048665088X   -->  true
X123456788   -->  false 
```

### 三、题解一

```
 function validISBN10(isbn) {

    var sum = 0;
    if(isbn.length !== 10) return false;
    for(let i = 0;i<isbn.length;i++){
      if(i == 9 && isbn.substr(i,1) == 'X'){
        sum += 100;
      }else{
        sum += isbn.substr(i,1) * (i+1)
      }
    }
    if(sum % 11 == 0) return true;
    return false;
} 
```

### 四、题解二

```
 const validISBN10 = isbn => isbn.length == 10 && isbn.split("").reduce((a, b, i) => a + (((b == "X") && (i == 9)) ? 10 : b) * (i + 1), 0) % 11 == 0; 
```