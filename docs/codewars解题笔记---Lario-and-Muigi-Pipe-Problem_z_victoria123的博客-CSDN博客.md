<!--yml
category: codewars
date: 2022-08-13 11:48:09
-->

# codewars解题笔记---Lario and Muigi Pipe Problem_z_victoria123的博客-CSDN博客

> 来源：[https://blog.csdn.net/z_victoria123/article/details/86607162?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-86607162.nonecase](https://blog.csdn.net/z_victoria123/article/details/86607162?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-86607162.nonecase)

题目

#Issue Looks like some hoodlum plumber and his brother has been running around and damaging your stages again.

The `pipes` connecting your level's stages together need to be fixed before you recieve any more complaints. Each pipe should be connecting, since the levels ascend, you can assume every number in the sequence after the first index will be greater than the previous and that there will be no duplicates.

#Task Given the a list of `numbers`, return the list so that the values increment by 1 for each index up to the maximum value.

#Example:

`Input: 1,3,5,6,7,8`

`Output: 1,2,3,4,5,6,7,8`

`解析`

`看起来像是某个流氓管道工和他的兄弟在到处乱跑，又破坏了你的舞台。`

`管道连接您的级别的阶段需要在您收到任何更多投诉之前修复。每个管道都应该连接，因为级别在上升，所以可以假定第一个索引之后的序列中的每个数字都将大于前一个索引，并且不会有重复的数据。`

`任务给定一个数字列表，返回该列表，使每个索引的值增加1，直至达到最大值。`

`我的答案`

```
 public static int[] pipeFix(int[] numbers) {
    // Fix the pipes!
    return  IntStream.rangeClosed(numbers[0],numbers[numbers.length-1]).toArray();
  }
```

最优答案

```
 public static int[] pipeFix(int[] numbers) {
    // Fix the pipes!
    return  IntStream.rangeClosed(numbers[0],numbers[numbers.length-1]).toArray();
  }
```

这是第一次和最优答案一样啊，安奈不住激动的心情，还是要多学，多看，像大佬们学习啊

在上一个其他答案

```
public static int[] pipeFix(int[] numbers) {
    int min = numbers[0];
    int max = numbers[numbers.length - 1];
    int size = max - min + 1;
    int[] result = new int[size];
    for (int i = 0; i < size; i++){
      result[i] = i + min;
    }
    return result;
  }
```