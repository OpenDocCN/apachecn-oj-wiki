<!--yml
category: codewars
date: 2022-08-13 11:49:26
-->

# Codewars第八天–Valid Braces_soufal的博客-CSDN博客

> 来源：[https://blog.csdn.net/u011562123/article/details/81911793?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-81911793.nonecase](https://blog.csdn.net/u011562123/article/details/81911793?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-81911793.nonecase)

## Codewars第八天–Valid Braces

题目描述：
这道题是常见的不同括号之间的匹配问题。给定一个括号序列，给出他是否匹配的结果，匹配则返回`True` ，否则返回`False` 。
例如：

```
"(){}[]"   =>  True
"([{}])"   =>  True
"(}"       =>  False
"[(])"     =>  False
"[({})](]" =>  False
```

代码如下：

```
def validBraces(string):
  result = []
  for i in string:
      if i in "({[":
          result.append(i)
      elif len(result) != 0:
          if (i == ')') & (result[-1] == '('):
              result.pop()
          elif (i == '}') & (result[-1] == '{'):
              result.pop()
          elif result[-1] == '[':
              result.pop()
  if len(result) == 0:
      return True
  else:
      return False
```

有一个非常简单的做法如下，不需要额外的栈来存储：

```
def validBraces(s):
  while '{}' in s or '()' in s or '[]' in s:
      s=s.replace('{}','')
      s=s.replace('[]','')
      s=s.replace('()','')
  return s==''
```

但是这个代码如果只有右括号`)` ，就会出现错误的判断，在codewar里面没有这样的实例，所以忽略了这一点。
改进代码如下：

```
def validBraces(string):
  result = []
  for i in string:
      if i in "({[":
          result.append(i)
      elif len(result) != 0:
          if (i == ')') & (result[-1] == '('):
              result.pop()
          elif (i == '}') & (result[-1] == '{'):
              result.pop()
          elif result[-1] == '[':
              result.pop()
      else:
          return False

  if len(result) == 0:
      return True
  else:
      return False

print(validBraces("))"))
```

这里也没有考虑有字母的情况，如果加上了字母，例如`test（）` 。则该代码会出错。继续修改为：

```
def validBraces(string):
  result = []
  for i in string:
      if i in "({[":
          result.append(i)
      elif len(result) != 0:
          if (i == ')') & (result[-1] == '('):
              result.pop()
          elif (i == '}') & (result[-1] == '{'):
              result.pop()
          elif result[-1] == '[':
              result.pop()
      elif i not in "(){}[]":
          continue
      else:
          return False

  if len(result) == 0:
      return True
  else:
      return False

print(validBraces("ttt(test()"))
```