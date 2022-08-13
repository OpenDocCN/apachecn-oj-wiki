<!--yml
category: codewars
date: 2022-08-13 11:43:35
-->

# 【Codewars JavaScript 5kyu】: Scramblies_小菜鸟快飞的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36362028/article/details/100547221?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-100547221.nonecase](https://blog.csdn.net/qq_36362028/article/details/100547221?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-100547221.nonecase)

# 问题描述：

Complete the function `scramble(str1, str2)` that returns `true` if a portion of `str1` characters can be rearranged to match `str2`, otherwise returns `false`.

**Notes:**

*   Only lower case letters will be used (a-z). No punctuation or digits will be included.
*   Performance needs to be considered

```
Input strings s1 and s2 are null terminated.
```

## Examples

```
scramble('rkqodlw', 'world') ==> True
scramble('cedewaraaossoqqyt', 'codewars') ==> True
scramble('katas', 'steak') ==> False
```

# 代码实现:

## js代码 

```
function scramble(str1, str2) {
    var count = Object.create(null);

    Array.prototype.forEach.call(str1, function(a) {
        count[a] = (count[a] || 0) + 1;
    });

    return Array.prototype.every.call(str2, function(a) {
        return count[a]--;
    });
}
```