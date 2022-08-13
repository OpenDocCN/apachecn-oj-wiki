<!--yml
category: codewars
date: 2022-08-13 11:46:01
-->

# Codewars第八天--Valid Parentheses(带有字母的单个括号匹配）_soufal的博客-CSDN博客

> 来源：[https://blog.csdn.net/u011562123/article/details/81913461?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-81913461.nonecase](https://blog.csdn.net/u011562123/article/details/81913461?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-81913461.nonecase)

## Codewars第八天–Valid Parentheses(带有字母的单个括号匹配）

题目描述：
该题只需要匹配一种括号，但是其中会有字母干扰。
比如测试用例为：

```
Test.assert_equals(valid_parentheses("  ("),False)
Test.assert_equals(valid_parentheses(")test"),False)
Test.assert_equals(valid_parentheses(""),True)
Test.assert_equals(valid_parentheses("hi())("),False)
Test.assert_equals(valid_parentheses("hi(hi)()"),True)
```

代码如下：

```
def valid_parentheses(string):
    stack = []
    for i in string:
        if i == '(':
            stack.append(i)
        elif i == ')' and len(stack) == 0:
            return False
        elif i == ')':
            stack.pop()
    return len(stack) == 0
```