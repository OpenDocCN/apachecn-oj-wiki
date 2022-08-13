<!--yml
category: codewars
date: 2022-08-13 11:33:47
-->

# Codewars刷题进阶---Js_eat_Cookie的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_39088036/article/details/105652191?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-105652191.142^v40^control,185^v2^control](https://blog.csdn.net/qq_39088036/article/details/105652191?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-105652191.142^v40^control,185^v2^control)

1.IP Validation

Write an algorithm that will identify valid IPv4 addresses in dot-decimal format. IPs should be considered valid if they consist of four octets, with values between `0` and `255`, inclusive.

Input to the function is guaranteed to be a single string.

### Examples

Valid inputs:

```
1.2.3.4
123.45.67.89
```

Invalid inputs:

```
1.2.3
1.2.3.4.5
123.456.78.90
123.045.067.089
```

Note that leading zeros (e.g. `01.02.03.04`) are considered invalid.

分析：题目意思很简单，按要求筛选合法ip地址

这里我们可以想到使用filter函数来进行过滤

筛选条件如下：

1.只有四个区间

2.每个区间的字符必须全部是数字

3.数字的范围在0-255

这里着重介绍一下第二个条件如何判断：

```
v==Numebr(v).toString();
```

完整代码如下：

```
function isValidIP(str) {
    return str.split('.').filter(function(v){return v==Number(v).toString() && Number(v)<256 && Number(v)>=0}).length==4;
}
```

这是反复学习修改过后的代码，来看看我第一次想到的代码：

```
function isValidIP(str) {
    var arrary = new Array();
    arrary = str.split('.');
    for(var i=0;i<arrary.length;i++){
        if (arrary[i]==""||arrary.length!=4) return false;
        for(var j=0;arrary[i].charAt(j)!="";j++){
            if(j>=1){
                if(arrary[i].charAt(0)=='0') return false;
            }
            if(arrary[i].charAt(j)<'0' || arrary[i].charAt(j)>'9') return false;
        }
            if(Number(arrary[i])>255 || Number(arrary[i])<0) return false;
    }
    return true;
} 
```

差距还是比较大的~

2.Pete, the baker

Pete likes to bake some cakes. He has some recipes and ingredients. Unfortunately he is not good in maths. Can you help him to find out, how many cakes he could bake considering his recipes?

Write a function `cakes()`, which takes the recipe (object) and the available ingredients (also an object) and returns the maximum number of cakes Pete can bake (integer). For simplicity there are no units for the amounts (e.g. 1 lb of flour or 200 g of sugar are simply 1 or 200). Ingredients that are not present in the objects, can be considered as 0.

Examples:

```
// must return 2
cakes({flour: 500, sugar: 200, eggs: 1}, {flour: 1200, sugar: 1200, eggs: 5, milk: 200}); 
```

思路分析：

思路很容易就想到了，主要看你会不会枚举Object属性，以及如何引用Object属性值

```
var obj = New Obejct();
for(var i in obj){
   console.log(i+" "+obj[i])
}
```

完整代码：

```
function cakes(recipe, available) {
    // TODO: insert code
    var num=0;
    for(var i in recipe){
        if(typeof available[i]=="undefined") return 0;
        else
        {
            var temp = Math.floor(available[i]/recipe[i]);
            if(num==0) num=temp;
            num =Math.min(num,temp);
        }
    }
    return num;
} 
```