<!--yml
category: codewars
date: 2022-08-13 11:43:54
-->

# Codewars第七天--Give me a Diamond_soufal的博客-CSDN博客

> 来源：[https://blog.csdn.net/u011562123/article/details/81867053?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-81867053.nonecase](https://blog.csdn.net/u011562123/article/details/81867053?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-81867053.nonecase)

## Codewars第七天–Give me a Diamond

题目描述：很简单的一道题，给定一个值`N` ,返回一个以`*` 构成的钻石形状的字符。
如果`n` 的值为偶数或者负数，则返回`None`。
如果`n=3` ，则输出：

```
 *
 ***
  *
```

具体代码如下：

```
def diamond(n):
    if n > 0 and n % 2 == 1:
        diamond = ""
        for i in range(n):
            diamond += " " * abs((n/2) - i)
            diamond += "*" * (n - abs((n-1) - 2 * i))
            diamond += "\n"
        return diamond
    else:
        return None
```

**在这里使用`abs()` 函数来返回数的绝对值，这样只需要一个`for` 循环就可以解决这个问题了。