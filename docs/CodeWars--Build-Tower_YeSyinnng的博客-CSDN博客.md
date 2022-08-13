<!--yml
category: codewars
date: 2022-08-13 11:42:27
-->

# CodeWars--Build Tower_YeSyinnng的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_39532595/article/details/86486433?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-14-86486433-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_39532595/article/details/86486433?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-14-86486433-null-null.142^v40^control,185^v2^control&utm_term=codewars)

题目：

> Build Tower by the following given argument:
> number of floors (integer and always greater than 0).
> Tower block is represented as *
> Python: return a list;
> JavaScript: returns an Array;
> C#: returns a string[];
> PHP: returns an array;
> C++: returns a vector;
> Haskell: returns a [String];
> Ruby: returns an Array;
> Have fun!

例子：

```
 *[   
     '     *     ',   1
     '    ***    ',   3
     '   *****   ',   5
     '  *******  ',   7
     ' ********* ',   9
     '***********'    11
     ]
     * 
```

解析题目： 开始的时候想要使用递归的方法进行使循环输出，然后通过正则表达式来进行替换，然而正则学的不太好。。 灵光一闪 想到了一个数组的方法

如下： 采用的是repeat方法~ 机智

```
function towerBuilder(nFloors) {
  var tower = [];
  for (var i = 0; i < nFloors; i++) {
    tower.push(" ".repeat(nFloors - i - 1)
             + "*".repeat((i * 2)+ 1)
             + " ".repeat(nFloors - i - 1));
  }
  return tower;
} 
```

大佬的代码：

```
function towerBuilder(n) {
  return Array.from({length: n}, function(v, k) {
    const spaces = ' '.repeat(n - k - 1);
    return spaces + '*'.repeat(k + k + 1) + spaces;
  });
} 
```

再接再励~