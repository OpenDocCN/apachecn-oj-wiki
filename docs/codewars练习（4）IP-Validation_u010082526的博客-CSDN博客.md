<!--yml
category: codewars
date: 2022-08-13 11:49:53
-->

# codewars练习（4）IP Validation_u010082526的博客-CSDN博客

> 来源：[https://blog.csdn.net/u010082526/article/details/85046197?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-85046197.nonecase](https://blog.csdn.net/u010082526/article/details/85046197?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-85046197.nonecase)

【1】计算字符串中包含字符个数

n=txt.count('ab')

参考[https://jingyan.baidu.com/article/48b37f8dfda0581a646488dd.html](https://jingyan.baidu.com/article/48b37f8dfda0581a646488dd.html)

【2】 is_valid_IP('a.255.56.1')报错

ValueError: invalid literal for int() with base 10: 'a'

解决方案：

[https://www.cnblogs.com/wangboqi/p/7455240.html](https://www.cnblogs.com/wangboqi/p/7455240.html)

是否数字str_1.isdigit()

是否字母str_1.isalpha()

```
是否数字和字母的组合str_1.isalnum()
```

【3】  is_valid_IP('022.255.56.1')输出不对

true

加入判断

    if val.index('0')==0:

报错

ValueError: substring not found

参考Python：查找字符在字符串中的位置

[https://blog.csdn.net/DeniuHe/article/details/77131150](https://blog.csdn.net/DeniuHe/article/details/77131150)

```
str_1.index(char_1)
```

在python语言中，如果想要知道某个字符串是否包含在列表中，可以直接使用index方法判断。如果包含了字符串中，返回该字符串第一次出现的位置；如果不包含，就会出错。

[https://jingyan.baidu.com/article/c33e3f48c275fcea15cbb506.html](https://jingyan.baidu.com/article/c33e3f48c275fcea15cbb506.html)

参考python中index()、find()方法

[https://blog.csdn.net/qq_39247153/article/details/81984431](https://blog.csdn.net/qq_39247153/article/details/81984431)

index() 方法检测字符串中是否包含子字符串 str ，如果指定 beg（开始） 和 end（结束） 范围，则检查是否包含在指定范围内，该方法与 python find()方法一样，**只不过如果str不在 string中会报一个异常。影响后面程序执行**

**[4]Test.assert_equals(is_valid_IP('0.0.0.0'),          True)返回错误**

**所以，加上是否大于0的判断**

                if int(val)>0 and val.find('0')==0:
                   print("False")
                   break

**最终代码如下：**

def is_valid_IP(strng):
  k=0
  if strng.count('.')!=3:
    return False
  else:
    a=strng.split('.')
    for val in a:
      if val.isdigit() and int(val)>=0 and int(val)<=255:
        if int(val)>0 and val.find('0')==0:
          return False
          break
        else:
          k+=1
      else:
        return False
        break
  if k==4:
    return True

别人的代码

import re def is_valid_IP(strng): return bool(re.match(r'^((\d{1,2}|1\d{2}|2[0-4]\d|25[0-5])(\.(?!$)|$)){4}(?=$)',strng))