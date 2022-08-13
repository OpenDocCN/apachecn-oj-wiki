<!--yml
category: codewars
date: 2022-08-13 11:39:30
-->

# codewars练习（javascript）-2021/2/19_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113861515?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-28-113861515-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/113861515?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-28-113861515-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/2/19

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Beginner - Lost Without a Map】

Given an array of integers, return a new array with each value doubled.

给定一个整数数组，返回一个新数组，每个值都加倍。

**<mark>example</mark>**：

```
[1, 2, 3] --> [2, 4, 6] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function maps(x){

      var result = JSON.parse(JSON.stringify(x))
      for(var i=0;i<result.length;i++){
        result.splice(i,1,result[i]*2)
      }
      return result;
    }

		console.log(maps([1,2,3])); </script> 
```

#### 【2】<7kyu>【Divide and Conquer】

Given a mixed array of number and string representations of integers, add up the string integers and subtract this from the total of the non-string integers.

给定一个由数字和字符串表示的整数混合数组，将字符串整数相加，然后从非字符串整数的总数中减去这个数。

**<mark>example</mark>**：

```
[9, 3, '7', '3']
['5', '0', 9, 3, 2, 1, '9', 6, 7] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function divCon(x){
      console.log(x)
      var temp = [];
      var tempA = [];
      var sum = 0;
      var sumS = 0;
      for(var i=0;i<x.length;i++){
        if(typeof x[i] == 'string'){

          temp.push(parseInt(x[i]))
        }else{
          tempA.push(x[i])
        }
      }

      for(var j=0;j<temp.length;j++){
        sum += temp[j];
      }
      for(var z=0;z<tempA.length;z++){
        sumS += tempA[z];
      }
      return sumS - sum;
    }

		console.log(divCon([9,3,'7','3']));
    console.log(divCon(['5', '0', 9, 3, 2, 1, '9', 6, 7])); </script> 
```

#### 【3】<7kyu>【Two numbers are positive】

Your job is to wite a function, which takes three integers `a`, `b`, and `c` as arguments, and returns `True` if exactly two of of the three integers are positive numbers, and `False` - otherwise.

**它以三个整数a、b和c作为参数，如果三个整数中恰好有两个是正数则返回True，否则返回False。**

**<mark>example</mark>**：

```
twoArePositive(2, 4, -3) == true
twoArePositive(-4, 6, 8) == true
twoArePositive(4, -6, 9) == true
twoArePositive(-4, 6, 0) == false
twoArePositive(4, 6, 10) == false
twoArePositive(-14, -3, -4) == false 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function twoArePositive(a, b, c) {

      var arr = [a,b,c];

      var num = 0
      for(var i=0;i<arr.length;i++){
        if(arr[i]>0)num ++;
      }
      if(num == 2)return true;
      return false;
    }

		console.log(twoArePositive(2,4,-3));
    console.log(twoArePositive(-4,6,8));
    console.log(twoArePositive(-14,-3,-4)); </script> 
```

#### 【4】<7kyu>【Clean up after your dog】

Given a 2D array to represent your garden, you must find and collect all of the dog cr@p - represented by ‘@’.

If you do, return ‘Clean’, else return ‘Cr@p’.

给定一个2D数组来代表你的花园，你必须找到并收集所有的狗cr@p -代表’@’。

**<mark>example</mark>**：

```
x=
[[_,_,_,_,_,_]
[_,_,_,_,@,_]
[@,_,_,_,_,_]]

bags = 2, cap = 2

return --> 'Clean' 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function crap(x, bags, cap){

      var numA = 0
      var numD = 0

      for(var i=0;i<x.length;i++){
        for(var j=0;j<x[i].length;j++)

          if(x[i][j] == '@')numA++;
          else if(x[i][j] == 'D') numD ++;
      }

      if(numD !=0)return 'Dog!!'
      else if(numA >cap)return 'Cr@p';
      else if(numA <= cap) return 'Clean'
    }

		console.log(crap([['_','_','_','_'], ['_','_','_','@'], ['_','_','@', '_']], 2, 2));
    console.log(crap([['_','_','_','_'], ['_','_','_','@'], ['_','_','@', '_']], 1, 1));
    console.log(crap([['_','_'], ['_','@'], ['D','_']], 2, 2)); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>