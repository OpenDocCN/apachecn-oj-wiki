<!--yml
category: codewars
date: 2022-08-13 11:36:28
-->

# codewars遇到的一些问题和总结_风凉ZZ的博客-CSDN博客

> 来源：[https://blog.csdn.net/The_X_One/article/details/87186889?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-87186889-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/The_X_One/article/details/87186889?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058716781683929565%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058716781683929565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-87186889-null-null.142^v40^control,185^v2^control&utm_term=codewars)

不定时更新中…

## 1\. Find the odd int

Description:Given an array, find the int that appears an odd number of times.
There will always be only one integer that appears an odd number of times.
这题目乍一看很简单的样子，吾等凡人的想法…循环一下就好…

```
function findOdd(A) {
  for(var i=0;i<A.length;i++){
    var num=0;
    for(var j=0;j<A.length;j++){
      if(A[i]===A[j]){
        num++;
      }
    }
    if(num%2===1){
      var result=A[i];
      break;
    }
  }
  return result;
} 
```

再看看最clever的解法，也是很干净简洁了…

```
const findOdd = (xs) => xs.reduce((a, b) => a ^ b); 
```

好像恍然大悟的样子…

* * *

关键点就是XOR中:a ^ b = c ， c ^ b = a ，c ^ a = b

```
eg:
A=[1,2,1,7,8,2,8,2,7]

1^2=3 -------------------------------------->1^2
    3^1=2 ---------------------------------->2
        2^7=5 ------------------------------>2^7
            5^8=13 ------------------------->2^7^8
                13^2=15 -------------------->7^8
                     15^8=7 ---------------->7
                          7^2=5 ------------>7^2
                              5^7=2 -------->2 
```

简单看起来就是：1 ^ 2 ^ 1 ^ 7 ^ 8 ^ 2 ^ 8 ^ 2 ^ 7,出现偶数次的数都抵消掉了，最后剩了个2。这个解法也是由于题目中给定了条件，数组中只有一个整数出现了奇数次。

* * *

## 2\. Roman Numerals Encoder

Description:Create a function taking a positive integer as its parameter and returning a string containing the Roman Numeral representation of that integer.

Modern Roman numerals are written by expressing each digit separately starting with the left most digit and skipping any digit with a value of zero. In Roman numerals 1990 is rendered: 1000=M, 900=CM, 90=XC; resulting in MCMXC. 2008 is written as 2000=MM, 8=VIII; or MMVIII. 1666 uses each Roman symbol in descending order: MDCLXVI.

Example:
solution(1000); // should return ‘M’

Help:
V — 5
X — 10
L — 50
C — 100
D — 500
M — 1,000
Remember that there can’t be more than 3 identical symbols in a row.
More about roman numerals - [http://en.wikipedia.org/wiki/Roman_numerals](http://en.wikipedia.org/wiki/Roman_numerals)
我一开始的想法是用递归，但是这样做的判断比较多，代码量比较大，感觉没有必要。后来就想用键值对的方式把数据存起来。
solution中clever票数最多的是这个：

```
function solution(number){
  // convert the number to a roman numeral
var  roman = {M:1000,CM:900, D:500,CD:400,C:100,XC:90,L:50,XL:40,X:10,IX:9,V:5,IV:4,I:1 }

var ans = '';
while(number>0){
    for(a in roman){ 
        if(roman[a]<=number){ ans += a; number-=roman[a]; break;}

    }
}
return ans;
} 
```

这个题依赖于键值对的顺序，在遍历的时候，要依照1000,900,500…这样的顺序遍历。但是对象是无序的，for-in 无法保证遍历顺序。所以我觉得这里用数组存数据会好一点。

```
function solution(number){
    // convert the number to a roman numeral
  decimals = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1];
  roman    = ['M', 'CM', 'D', 'CD', 'C', 'XC', 'L', 'XL', 'X', 'IX', 'V', 'IV', 'I'];
  var ans = '';
  while(number>0){
      for(index in decimals){ 
          if(decimals[index]<=number){ ans += roman[index]; number-=decimals[index]; break;}
      }
  }
  return ans;
} 
```