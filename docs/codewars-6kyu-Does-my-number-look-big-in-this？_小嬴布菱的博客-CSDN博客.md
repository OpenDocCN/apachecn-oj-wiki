<!--yml
category: codewars
date: 2022-08-13 11:38:31
-->

# codewars 6kyu Does my number look big in this?_小嬴布菱的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_29549685/article/details/117411035?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-30-117411035-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_29549685/article/details/117411035?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-30-117411035-null-null.142^v40^control,185^v2^control&utm_term=codewars)

codewars [6kyu Does my number look big in this?](https://www.codewars.com/kata/5287e858c6b5a9678200083c/solutions/javascript)

题目大意：判断一个数是否是水仙花数。

```
function narcissistic(value) {

  var temp = String(value).split("");
  var ans = 0;
  var n = temp.length;
  for (let i = 0; i < n; i++) {
    ans += Math.pow(temp[i], n);
  }
  return ans == value;
} 
```

别人的题解，和我的一个意思，只不过他们用的感觉更像JS。

```
function narcissistic(value) {
  return (
    ("" + value).split("").reduce(function (p, c) {
      return p + Math.pow(c, ("" + value).length);
    }, 0) == value
  );
} 
```

```
function narcissistic(value) {
  return (
    value
      .toString()
      .split("")
      .map((x, i, arr) => x ** arr.length)
      .reduce((a, b) => +a + +b) === value
  );
}

narcissistic = (num) =>
  num
    .toString()
    .split("")
    .reduce(function (prev, el) {
      return prev + Math.pow(el, String(num).length);
    }, 0) == num; 
```