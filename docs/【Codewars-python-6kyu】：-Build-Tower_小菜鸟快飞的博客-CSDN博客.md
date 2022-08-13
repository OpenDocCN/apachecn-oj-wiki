<!--yml
category: codewars
date: 2022-08-13 11:45:39
-->

# 【Codewars python 6kyu】: Build Tower_小菜鸟快飞的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36362028/article/details/100547117?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-100547117.nonecase](https://blog.csdn.net/qq_36362028/article/details/100547117?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-100547117.nonecase)

# 问题描述：

## Build Tower

Build Tower by the following given argument:
**number of floors** (integer and always greater than 0).

Tower block is represented as `*`

*   Python: return a `list`;
*   JavaScript: returns an `Array`;
*   C#: returns a `string[]`;
*   PHP: returns an `array`;
*   C++: returns a `vector<string>`;
*   Haskell: returns a `[String]`;
*   Ruby: returns an `Array`;

Have fun!

* * *

for example, a tower of 3 floors looks like below

```
[
  '  *  ', 
  ' *** ', 
  '*****'
]
```

and a tower of 6 floors looks like below

```
[
  '     *     ', 
  '    ***    ', 
  '   *****   ', 
  '  *******  ', 
  ' ********* ', 
  '***********'
]
```

# 代码实现：

```
#codewars第六题
def tower_builder(n_floors):
    # build here
    new_list = []
    for i in range(1,n_floors+1):
        new_list.append(' '*(n_floors-i) + '*'*(2*i-1) + ' '*(n_floors-i))  #直接在空列表中追加  注意 ' '*n + 'X'*2 的字符串的使用
    return new_list

#另解
def tower_builder(n):
    return [("*" * (i*2-1)).center(n-i) for i in range(1, n+1)]  #s.center(width,"str")是整个len为width，两边用str填充，中间是s

tower_builder(6)
```