<!--yml
category: codewars
date: 2022-08-13 11:44:27
-->

# codewars 4ky Sum of Intervals_小嬴布菱的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_29549685/article/details/117455431?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-117455431.nonecase](https://blog.csdn.net/qq_29549685/article/details/117455431?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-117455431.nonecase)

### 题目大意：

给定一个数组，这个数组是由如[3,5]这样的区间 Array 组成的，求区间的长度。如果区间之间有交叉，那么不重复计算交叉部分。
如果给定的数组为：[[1,5],[2,6]]，那么这个相当于是计算区间[1,6]，这个区间的长度为 5。

### 我的思路:

将区间先进行排序（这个地方卡了很久，难受），排序后得到的有序区间，可以比较前一个区间的右端和后一个区间的左端，如果后一个区间的左端小于前一个区间的右端，证明这两个区间有交叉部分，那么合并这两个区间。最后逐一处理每个区间得到答案。

这里的排序我一定要讲一下，不知道是不是 node 版本不一样的原因，我在 vscode 里怎么测试都没问题，但是在提交的时候总是不能通过。最后 console.log 了一下，才发现是 sort 这里不对，应该是我学的还不够。我写了一个新的 sortinter 函数来处理这个区间排序。本以为是个简单题，没想到写了 2 个小时。难受。没错，排序算法又忘记了，重新复习了，十分随便的写了个冒泡，真菜。。。

合并区间这里也有几个需要注意的地方，详见代码注释。

```
function sumIntervals(intervals) {

  var ans = 0;
  intervals = sortinter(intervals);
  console.log("sort:", intervals);
  for (var i = 0; i < intervals.length - 1; i++) {
    if (intervals[i][1] >= intervals[i + 1][0]) {
      var a = intervals[i][0],
        b = Math.max(intervals[i + 1][1], intervals[i][1]); 
      intervals.splice(i, 2); 
      console.log(i, intervals);
      intervals.splice(i, 0, [a, b]); 
      console.log(i, intervals);
      i -= 1; 
    }
  }
  for (q of intervals) {
    ans += q[1] - q[0];
  }
  return ans;
}

var sortinter = function (list) {
  for (var i = 0; i < list.length - 1; i++) {
    for (var j = 0; j < list.length - 1 - i; j++) {
      if (list[j][0] > list[j + 1][0]) {
        var temp = list[j + 1];
        list[j + 1] = list[j];
        list[j] = temp;
      }
    }
  }
  return list;
}; 
```

### 其他思路

看到大佬们的解法，又发现了巧妙的方法:

1.  直接把各个区间范围的数扔到一个**集合**里！！然后统计集合的长度就可以了。
    ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。
    Array.from 方法可以将 Set 结构转为数组。可以专门编写使用一个去重的函数

    ```
    function sumIntervals(intervals) {
      const ranges = new Set();
      intervals.forEach(([start, end]) => {
        for (let i = start; i < end; i++) ranges.add(i);
      });
      return ranges.size;
    }

    const sumIntervals = (intervals) =>
      new Set(
        [].concat(
          ...intervals.map(([a, b]) =>
            [...Array(b - a)].map((_, idx) => a + idx)
          )
        )
      ).size; 
    ```

    另外 Set 非常强大，使用 Set 可以很容易地实现并集（Union）、交集（Intersect）和差集（Difference）。

2.  创建一个空数组，把范围内的数扔到这个空数组里，再用 indexOf 去重。

    ```
    function sumIntervals(intervals) {
      var numbers = [];
      intervals.forEach(function (interval) {
        for (var i = interval[0]; i < interval[1]; i++) {
          if (numbers.indexOf(i) == -1) numbers.push(i);
        }
      });
      return numbers.length;
    } 
    ```

3.  建立一个字典，将范围内的数都存为键值，最后统计一下键值对个数即可。

    ```
    function sumIntervals(intervals) {
      var numbers = {};
      intervals.forEach(function (x) {
        for (var i = x[0]; i < x[1]; i++) {
          numbers[i] = i;
        }
      });
      return Object.keys(numbers).length;
    } 
    ```

4.  普通方法的精简版本：

    ```
    const sumIntervals = (intervals) => {
      intervals.sort((p, n) => p[1] - n[1]);

      for (let i = 0; i < intervals.length - 1; i++) {
        if (intervals[i][1] > intervals[i + 1][0]) {
          intervals[i][0] = Math.min(intervals[i][0], intervals[i + 1][0]);
          intervals[i][1] = intervals[i + 1][1];
          intervals.splice(i + 1, 1);
          i = -1;
        }
      }
      return intervals.reduce((a, v) => a + (v[1] - v[0]), 0);
    }; 
    ```

### 总结

1.  读完题以后可以先思考一下有没有什么巧妙的办法偷懒。
2.  debug 真的很重要。
3.  需要复习一下排序算法，人家的 sort 怎么就没问题呢？！
4.  ES6 中的 Set()也需要好好学一下。
5.  去重的方法总结：