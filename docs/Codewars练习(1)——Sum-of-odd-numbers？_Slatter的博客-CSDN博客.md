<!--yml
category: codewars
date: 2022-08-13 11:49:49
-->

# Codewars练习(1)——Sum of odd numbers?_Slatter的博客-CSDN博客

> 来源：[https://blog.csdn.net/Slatter/article/details/94362162?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-94362162.nonecase](https://blog.csdn.net/Slatter/article/details/94362162?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-94362162.nonecase)

### 每周写Codewars的宗旨：多刷Codewars,多虐自己一点点，每周提升多一点

个人觉得Codewars都做的还挺好的，就是在它那个页面写代码不自带缩进很难受，所以我运行成功的代码都复制到Vscode里面调整好再放到代码块里的
**Codewars：Kata 7kyu——Sum of odd numbers?**
**题目要求：**
Given the triangle of consecutive odd numbers:

```
 1
          3     5
       7     9    11
   13    15    17    19
21    23    25    27    29
... 
```

Calculate the row sums of this triangle from the row index (starting at index 1) e.g.:

```
rowSumOddNumbers(1); // 1
rowSumOddNumbers(2); // 3 + 5 = 8 
```

**C++编写：**

```
long long rowSumOddNumbers(unsigned n){
    if(n == 1)  return 1;
    else
    {
        int m = n*(n-1)+1;
        int k = n/2;
        if(n%2 == 1)
        {
            return (m+k*2)*n;
        }
        else
        {
            return (m+n-1)*n;
        } 
    } 
} 
```

本来第一题我是打的Kata 6kyu——Is a number prime的，不过我真的是被虐的够惨，无论怎么打都是超时，没办法，第一个练个简单的，其实这道题要说难还是有一定的难度，要说简单也很简单，讲解一下我的思路：
**思路：**
这道题其实就类似于初高中的找规律求第几行第几个数是多少的题。不难看出其实每一行的和都可以是一个平均数乘上行数，那么我们要找到这个平均数是多少，只要知道该行的第一个数是多少就可以了。那么每行的第一个数就等于：行数×(行数-1)+1，也就是代码中的`m = n*(n-1)+1`；那么如果行数是奇数行，那么那个平均数大小就为：该行第一个数+(行数/2)×2，注意此处的（行数/2）的值是等于该运算所得值的整数部分，对应代码中的`m+k*2`；而如果行数是奇数，那么这个平均数大小就等于：该行第一个数+行数-1，对应代码中的`m+n-1`；那么最后将平均数乘上行数就是答案了。当然第一行是个例外，单独写出即可。