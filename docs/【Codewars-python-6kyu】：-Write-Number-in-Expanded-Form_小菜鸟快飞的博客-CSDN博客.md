<!--yml
category: codewars
date: 2022-08-13 11:51:33
-->

# 【Codewars python 6kyu】: Write Number in Expanded Form_小菜鸟快飞的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36362028/article/details/100547371?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-100547371.nonecase](https://blog.csdn.net/qq_36362028/article/details/100547371?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-100547371.nonecase)

# 问题描述：

# Write Number in Expanded Form

You will be given a number and you will need to return it as a string in [Expanded Form](https://www.mathplacementreview.com/arithmetic/whole-numbers.php#expanded-form). For example:

```
expanded_form(12) # Should return '10 + 2'
expanded_form(42) # Should return '40 + 2'
expanded_form(70304) # Should return '70000 + 300 + 4'
```

NOTE: All numbers will be whole numbers greater than 0.

If you liked this kata, check out [part 2](https://www.codewars.com/kata/write-number-in-expanded-form-part-2)!!

代码实现：

```
#codewars第十一题
def expanded_form(num):
    my_str = str(num)
    _length = len(my_str)
    j = 0
    res = ''
    if _length == 1: return str(num)
    for item in my_str:
        _length -= 1
        if int(item) == 0: continue
        if j == 0:
            res += str(int(item) * pow(10,_length))
            j += 1
        else:
            res += ' + '
            res += str(int(item) * pow(10,_length))
    return res

#另解
def expanded_form(num):
    num = list(str(num))
    return ' + '.join(x + '0' * (len(num) - y - 1) for y,x in enumerate(num) if x != '0')  #注意join()的用法   enumerate()枚举

expanded_form(334949)
```