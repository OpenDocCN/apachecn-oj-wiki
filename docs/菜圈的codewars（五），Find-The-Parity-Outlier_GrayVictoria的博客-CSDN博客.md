<!--yml
category: codewars
date: 2022-08-13 11:50:13
-->

# 菜圈的codewars（五），Find The Parity Outlier_GrayVictoria的博客-CSDN博客

> 来源：[https://blog.csdn.net/GrayVictoria/article/details/51321643?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-51321643.nonecase](https://blog.csdn.net/GrayVictoria/article/details/51321643?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-51321643.nonecase)

这题的意思是从一堆奇数里挑偶数，一堆偶数里挑奇数，还算简单。

```
def find_outlier(integers):
	odd,even=0,0
	oddnum,evennum=0,0
	for x in integers:
		if(x%2==0):
			evennum=x
			even=even+1
		else:
			oddnum=x
			odd=odd+1
	if even==len(integers)-1:
		return oddnum
	else:
		return evennum
```

贴一个大神的代码：

```
def find_outlier(int):
    odds = [x for x in int if x%2!=0]
    evens= [x for x in int if x%2==0]
    return odds[0] if len(odds)<len(evens) else evens[0]
```

有点厉害，这种应该是已经熟练掌握的了吧

在这里刷题最坏也是最好的一点就是每道题只能自己做出来，谁都帮不了你，答案都是找不到的，bug只能自己zhai