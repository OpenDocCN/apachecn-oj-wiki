<!--yml
category: codewars
date: 2022-08-13 11:42:49
-->

# codewars 7_kyu Is this a triangle_小嬴布菱的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_29549685/article/details/117340045?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-25-117340045-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_29549685/article/details/117340045?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-25-117340045-null-null.142^v40^control,185^v2^control&utm_term=codewars)

codewars [7_kyu Is this a triangle?](https://www.codewars.com/kata/56606694ec01347ce800001b/train/javascript)

题目大意：给定 3 个整数为三角形的三条边，判定这三条边能否组成一个三角形。

我的解法就是高中数学判定一下。

```
function isTriangle(a, b, c) {
  if (a + b > c && a + c > b && b + c > a) {
    return true;
  }
  return false;
} 
```

没错，又到了公开处刑的环节，人家怎么都能一句话写出来呢！！

```
function isTriangle(a, b, c) {
  return a + b > c && a + c > b && c + b > a;
}

var isTriangle = (a, b, c) => Math.max(a, b, c) < (a + b + c) / 2;

function isTriangle(a, b, c) {
  [a, b, c] = [a, b, c].sort((x, y) => x - y);
  return a + b > c;
} 
```