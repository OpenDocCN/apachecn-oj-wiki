<!--yml
category: codewars
date: 2022-08-13 11:39:32
-->

# codewars 6 kyu Sort the odd_小嬴布菱的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_29549685/article/details/117487143?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-29-117487143-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_29549685/article/details/117487143?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-29-117487143-null-null.142^v40^control,185^v2^control&utm_term=codewars)

### 题目大意

给定一个数组，将其中的奇数排序，偶数的位置不变。

### 我的思路

创建两个新的数组 ans 和 odd。odd 数组，用于存奇数并排序；ans 为结果数组。先遍历一遍 array 数组，如果是奇数，将该数存入 odd 数组，并且存入对应位的 ans 存负无穷，否则 ans 存入遍历到的偶数。然后将 odd 中的数排序，最后遍历 ans 数组，如果该位为负无穷，将 odd 中第一位 shift 出并存到 ans。

```
function sortArray(array) {

  var ans = [],
    odd = [];
  console.log(array, ans, odd);
  for (let i = 0; i < array.length; i++) {
    if (array[i] % 2 != 0) {
      ans[i] = -Infinity;
      odd.push(array[i]);
    } else {
      ans[i] = array[i];
    }

  }
  odd.sort(function (a, b) {
    return a - b;
  });
  console.log(odd);
  for (let i = 0; i < array.length; i++) {
    if (ans[i] == -Infinity) {
      ans[i] = odd.shift();
    }
  }
  return ans;
} 
```

### 优秀的题解

这个题解用了 filter，还使用了 map，思路应该是差不多的，但是这么精简的写法还是需要努力学习的！

```
function sortArray(array) {
  const odd = array.filter((x) => x % 2).sort((a, b) => a - b);
  return array.map((x) => (x % 2 ? odd.shift() : x));
} 
```