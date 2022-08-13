<!--yml
category: codewars
date: 2022-08-13 11:47:31
-->

# Codewars算法题（5）_哆啦AA梦的博客-CSDN博客

> 来源：[https://blog.csdn.net/y1535766478/article/details/76102649?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-76102649.nonecase](https://blog.csdn.net/y1535766478/article/details/76102649?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-76102649.nonecase)

第18题：(printer_error)

问题：

In a factory a printer prints labels for boxes. For one kind of boxes the printer has to use colors which, for the sake of simplicity, are named with letters from `a to m`.

The colors used by the printer are recorded in a control string. For example a "good" control string would be `aaabbbbhaijjjm` meaning that the printer used three times color a, four times color b, one time color h then one time color a...

Sometimes there are problems: lack of colors, technical malfunction and a "bad" control string is produced e.g. `aaaxbbbbyyhwawiwjjjwwm`.

You have to write a function `printer_error` which given a string will output the error rate of the printer as a string representing a rational whose numerator is the number of errors and the denominator the length of the control string. Don't reduce this fraction to a simpler expression.

The string has a length greater or equal to one and contains only letters from `a`to `z`.

#Examples:

```
s="aaabbbbhaijjjm"
error_printer(s) => "0/14"

s="aaaxbbbbyyhwawiwjjjwwm"
error_printer(s) => "8/22"
```

问题描述：

其实说简单了就是找出一个字符串中不在‘abcdefghijklm’中的个数，并返回其所占的比例

代码实现：

```
**def** **printer_error**(s):
  c=0
  **for** i **in** range(0,len(s)):
  **if** s[i] **not in** 'abcdefghijklm':
  c+=1
  **return** str(c)+"/"+str(len(s))
```

评分较高代码：

（1）

```
**from** re **import** sub
**def** **printer_error**(s):
  **return** "{}/{}".format(len(sub("[a-m]",'',s)),len(s)
```

```
在此简单解释一下sub()函数，sub()函数中第一个参数是要替换掉的字符，第二个参数是用什么替换，第三个参数是
```

```
 替换哪个字符串的字符，该例中实现的是将s字符串中的[a-m]替换成空。具体使用方法可参见[博客](http://www.cnblogs.com/ToDoToTry/p/5635863.html)
```

```
format()函数实现格式化将format中的参数按前面”{}/{}”格式输出。
```

```
（2）
```

```
 ```
**def** **printer_error**(s):
  **return** "%s/%s" % (len(s.translate(None, "abcdefghijklm")), len(s))
```

该方法中使用了translate（）函数，将s字符串中的“abcdefghijklm”删除，与方法一异曲同工
```

```
（3）
```

```
 ```
**def** **printer_error**(s):
  **import** re
    **return** str(len(re.findall('[n-z]', s))) + "/" + str(len(s))
```

该方法用了findall()函数,方法详解见[博客](http://blog.csdn.net/cashey1991/article/details/8875213)
```

```
（4）
```

```
 ```
**def** **printer_error**(s):   s1 = len([ x **for** x **in** s **if** ord(x) > ord('m')])
    **return** str(s1) +'/' + str(len(s))
```

第19题（切巧克力问题）
```

```
问题：
```

```
 ##### Description:

Your task is to split the chocolate bar of given dimension `n` x `m` into small squares. Each square is of size 1x1 and unbreakable. Implement a 

function that will return minimum number of breaks needed.

For example if you are given a chocolate bar of size `2` x `1` you can split it to single squares in just one break, but for size `3` x `1` you must do two breaks.

If input data is invalid you should return 0 (as in no breaks are needed if we do not have any chocolate to split). Input will always be a non-negative integer.

 代码实现：
```

```
 ```
**def** **breakChocolate**(n, m):
  **return** ((n * m - 1) **if** n * m > 1 **else** 0)
``` 
```

```
评分较高代码：
```

```
 ```
**def** **breakChocolate**(n, m):
  **return** max(n * m - 1, 0)
```

这一题很简单不做过多解释
```

```
201707261335 持续更新中~~~
```