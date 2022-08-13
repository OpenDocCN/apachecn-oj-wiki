<!--yml
category: codewars
date: 2022-08-13 11:40:30
-->

# codewars练习（javascript）-2021/2/18_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113854705?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-20-113854705-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/113854705?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-20-113854705-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/2/18

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Switcheroo】

Given a string made up of letters a, b, and/or c, switch the position of letters a and b (change a to b and vice versa). Leave any incidence of c untouched.

**切换字母a和b的位置**

**<mark>example</mark>**：

```
'acb'
'aabacbaa' 
'ccccc' 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function switcheroo(x){

      var t = /[a|b]/.test(x);
      if(t){
        var arr = x.split('');

        for(var i=0;i<arr.length;i++){
          if(arr[i]=='a')arr[i]='b';
          else if(arr[i] =='b')arr[i] = 'a';

        }
        return arr.join('');
      }else{
        return x;
      }
    }

		console.log(switcheroo('abc'));
    console.log(switcheroo('aaabcccbaaa'));
    console.log(switcheroo('ccccc'));
    console.log(switcheroo('ab')); </script> 
```

#### 【2】<7kyu>【Double Trouble】

Given an array of integers (x), and a target (t), you must find out if any two consecutive numbers in the array sum to t. If so, remove the second number.

**给定一个由整数(x)和目标(t)组成的数组，你必须找出数组中任意两个连续的数字是否和为t。如果是，删除第二个数字。**

**<mark>example</mark>**：

```
x = [1, 2, 3, 4, 5]
t = 3

1+2 = t, so remove 2. No other pairs = t, so rest of array remains:

[1, 3, 4, 5] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function trouble(x, t){

      for(var i=0;i<x.length;i++){
        for(var j=i+1;j<i+2;j++){
          if(x[i] + x[j] == t){
            x.splice(j,1);

            j--;
          }
        }

      }
      return x;
    }

		console.log(trouble([1, 3, 5, 6, 7, 4, 3],7));
    console.log(trouble([4, 1, 1, 1, 4],2));
    console.log(trouble([2, 2, 2, 2, 2, 2], 4)); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>