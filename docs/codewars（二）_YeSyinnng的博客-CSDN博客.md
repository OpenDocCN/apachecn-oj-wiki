<!--yml
category: codewars
date: 2022-08-13 11:40:15
-->

# codewars（二）_YeSyinnng的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_39532595/article/details/85333235?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-12-85333235-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_39532595/article/details/85333235?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-12-85333235-null-null.142^v40^control,185^v2^control&utm_term=codewars)

今天是体验codewars的第二天，今天开始研究了一下大佬们的代码，emm，for循环是恶魔吧，我要换换换~！！

今天的题目：

> //您将获得一个包含整数的数组（其长度至少为3，但可能非常大）。除了单个整数之外，该数组要么完全由奇数整数组成，要么完全由偶数整数组成N。编写一个方法，将数组作为参数并返回此“异常值”
> N。 // You are given an array (which will have a length of at least
> 3, but could be very large) containing integers. The array is either
> entirely comprised of odd integers or entirely comprised of even
> integers except for a single integer N. Write a method that takes the
> array as an argument and returns this “outlier” N.

emm，
（1）数组作为一个参数，并且长度大于3 先判断是否大于3
（2） 判断奇数/偶数输出不属于一类的数字，并且存入到数组中 作为返回值输出
（3） 判断奇数和偶数 然后比较长度 进行输出
这是我的想法，最开始的想法，后来，发现看错题目了，，只要输出一个数字就好，注意，是数字。。这就是第一次提交没过的原因啊~
第一次代码：

```
 function findOutlier(integers){
        var arrBlock1 =[];
        var arrBlock2 =[];
        if(integers.length>2){
            for(var i=0;i<integers.length;i++){
                if(integers[i] % 2 ===0){
                    arrBlock1.push(integers[i]);
                }else {
                    arrBlock2.push(integers[i]);
                }
            }
            integers=parseInt(arrBlock1.length<arrBlock2.length?arrBlock1:arrBlock2);
        }
        return integers;
    } 
```

代码已经发现了我的菜。。

第二次代码（ps：看过大佬代码的思路）：
用filter才是王道。。。

```
 function findOutlier1(integers) {
        return integers.slice(0, 3).filter(even).length >= 2 ? integers.find(odd) : integers.find(even)
    }
    const even = (num) => {
        return (num % 2 === 0)
    }
    const odd = (num) => {
        return (num % 2 !== 0)
    } 
```

得票最高的代码：

```
function findOutlier(int){
  var even = int.filter(a=>a%2==0);
  var odd = int.filter(a=>a%2!==0);
  return even.length==1? even[0] : odd[0];
} 
```

嘻嘻 其实差不多啦，继续加油啦~~