<!--yml
category: codewars
date: 2022-08-13 11:50:24
-->

# 菜圈的codewars（八），Replace With Alphabet Position_GrayVictoria的博客-CSDN博客

> 来源：[https://blog.csdn.net/GrayVictoria/article/details/51333024?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-51333024.nonecase](https://blog.csdn.net/GrayVictoria/article/details/51333024?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-51333024.nonecase)

##### Description:

Welcome. In this kata you are required to, given a string, replace every letter with its position in the alphabet. If anything in the text isn't a letter, ignore it and don't return it. a being 1, b being 2, etc. As an example:

```
alphabet_position("The sunset sets at twelve o' clock.")
```

Should return `"20 8 5 19 21 14 19 5 20 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11"` (As a string.)

竟然写出了一个和大神差不多思路的代码……好激动

但其实就是找度娘百度了几个函数= =

```
import re
def alphabet_position(text):
	text=re.sub('[^a-zA-Z]','',text) #delete all inalphabet
	text=text.lower()
	m=[]
	for x in text:
		m.append(str(ord(x)-ord('a')+1))
	m=' '.join(m)
	print m
	return m
```

感觉自己的英语水平在进步……

我竟然用英语恢复了两个外国小伙伴……