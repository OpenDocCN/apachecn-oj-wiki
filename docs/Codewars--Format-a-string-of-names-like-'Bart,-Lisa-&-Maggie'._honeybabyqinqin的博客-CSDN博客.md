<!--yml
category: codewars
date: 2022-08-13 11:50:52
-->

# Codewars--Format a string of names like 'Bart, Lisa & Maggie'._honeybabyqinqin的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41871914/article/details/85005265?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-85005265.nonecase](https://blog.csdn.net/weixin_41871914/article/details/85005265?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-85005265.nonecase)

# Format a string of names like ‘Bart, Lisa & Maggie’.

## Problem Description:

![在这里插入图片描述](img/6c86926a793eb4210e51453fa5f45375.png)
Given: an array containing hashes of names

Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.

Example:
![在这里插入图片描述](img/3b3cd4161ea41e2f1a78a1a40c7049cd.png)

Note: all the hashes are pre-validated and will only contain A-Z, a-z, ‘-’ and ‘.’.

#### Sample Test:

```
Test.assert_equals(namelist([{'name': 'Bart'},{'name': 'Lisa'},{'name': 'Maggie'},{'name': 'Homer'},{'name': 'Marge'}]), 'Bart, Lisa, Maggie, Homer & Marge',
"Must work with many names")
Test.assert_equals(namelist([{'name': 'Bart'},{'name': 'Lisa'},{'name': 'Maggie'}]), 'Bart, Lisa & Maggie',
"Must work with many names")
Test.assert_equals(namelist([{'name': 'Bart'},{'name': 'Lisa'}]), 'Bart & Lisa', 
"Must work with two names")
Test.assert_equals(namelist([{'name': 'Bart'}]), 'Bart', "Wrong output for a single name")
Test.assert_equals(namelist([]), '', "Must work with no names") 
```

# Version of Python:

![在这里插入图片描述](img/2f92ea8407e154d29dd2ec29f64f2d41.png)

# Solution:

```
def namelist(names):
    #your code here
    toReturn = ''
    if(len(names) == 1):
        return names[0]['name']
    elif(len(names) == 2):
        toReturn = toReturn + names[0]['name'] + " & " + names[1]['name']
    elif(len(names) > 2):
        for i in range(0, len(names)-1):
            toReturn = toReturn + names[i]['name'] + ", "
        toReturn = toReturn[:-2] + " & " + names[len(names)-1]['name']
    return toReturn 
```

![在这里插入图片描述](img/0fa07c11e6e1f59cd65284a5ed878a0e.png)