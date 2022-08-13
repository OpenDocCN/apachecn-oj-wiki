<!--yml
category: codewars
date: 2022-08-13 11:45:17
-->

# codewars 5 kyu Maximum subarray sum_小嬴布菱的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_29549685/article/details/117535172?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-117535172.nonecase](https://blog.csdn.net/qq_29549685/article/details/117535172?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-117535172.nonecase)

### 我的思路

最开始的思路是使用前缀和，找到最大和最小的前缀和一减不就行了，然后发现我这么写不对劲，有可能最小的前缀和在最大的前缀和的后面。

```
var maxSequence = function (arr) {

  console.log(arr);
  if (arr.length <= 1) return arr.length;
  var prefix = [];
  prefix[0] = arr[0];
  var left = prefix[0],
    right = prefix[0];
  for (let i = 1; i < arr.length; i++) {
    prefix[i] = prefix[i - 1] + arr[i];
    left = Math.min(left, prefix[i]);
    right = Math.max(right, prefix[i]);
  }
  console.log(prefix, left, right);
  return prefix[arr.length - 1] > right - left
    ? prefix[arr.length - 1]
    : right < 0
    ? 0
    : right - left;
}; 
```

当然也可以暴力破解，感觉可能会超时并没有使用这个方法。
又想了一下，是不是可以操作一下前缀和？

```
var maxSequence = function (arr) {

  var prefix = [];
  prefix[-1] = 0;
  for (let i = 0; i < arr.length; i++) {
    prefix[i] =
      prefix[i - 1] + arr[i] > arr[i] ? prefix[i - 1] + arr[i] : arr[i];
  }
  var ans = 0;
  for (let i = 0; i < prefix.length; i++) {
    if (ans < prefix[i]) ans = prefix[i];
  }
  return ans;
}; 
```

在这里可以用一个变量来代替数组 prefix。

```
var maxSequence = function (arr) {
  var ans = 0;
  var thisMax = 0;
  for (let i = 0; i < arr.length; i++) {
    thisMax += arr[i];
    if (thisMax < arr[i]) thisMax = arr[i];
    if (thisMax > ans) ans = thisMax;
  }
  return ans;
}; 
```

### 其他大佬解法

```
 var maxSequence = function (arr) {
  var min = 0,
    ans = 0,
    sum = 0;
  for (var i = 0; i < arr.length; ++i) {
    sum += arr[i];
    min = Math.min(sum, min);
    ans = Math.max(ans, sum - min);
  }
  return ans;
}; 
```

```
var maxSequence = function (arr) {
  var max = 0;
  var cur = 0;
  arr.forEach(function (i) {
    cur = Math.max(0, cur + i);
    max = Math.max(max, cur);
  });
  return max;
}; 
```

```
function maxSequence(arr) {
  var max = 0;

  for (var i = 0; i < arr.length; i++) {
    for (var sum = 0, j = i; j < arr.length; j++) {
      sum += arr[j];
      if (sum > max) max = sum;
    }
  }

  return max;
}

var maxSequence = function (arr) {
  var max = 0;
  for (var i = 0; i < arr.length; i++) {
    for (var j = arr.length; j > i; j--) {
      var total = arr.slice(i, j).reduce(function (a, b) {
        return a + b;
      });
      if (max < total) max = total;
    }
  }
  return max;
};

var maxSequence = function (arr) {
  var max = 0;
  for (var i = 0; i < arr.length; i++) {
    for (var j = arr.length; j > i; j--) {
      var total = arr.slice(i, j).reduce(function (a, b) {
        return a + b;
      });
      if (max < total) max = total;
    }
  }
  return max;
}; 
```