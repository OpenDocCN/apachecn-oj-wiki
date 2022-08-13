<!--yml
category: codewars
date: 2022-08-13 11:44:14
-->

# Codewars：Balanced Numbers_青草封尘的博客-CSDN博客

> 来源：[https://blog.csdn.net/w1961557599/article/details/100594561?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-100594561.nonecase](https://blog.csdn.net/w1961557599/article/details/100594561?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-100594561.nonecase)

**题目描述：
给出一个数，当他的左边各个位上的数字加起来与右边各个位上的 数字加起来相等时，即为Balanced Number；**

example1：23450
example2：234
example3：157824

Balanced ; Not Balanced ; Balanced

```
#include<stdio.h>
int main(void)
{
	int number;
	scanf("%d",&number);
	int i,j,leftsum=0,rightsum=0,cnt[20];

	for(i=0;number/10!=0;i++)
	{
		cnt[i]=number%!0;
		number/=10;
	}
	cnt[i]=number;

	for(j=0;j<i/2;j++)\
	{
		rightsum+=cnt[j]
		leftsum+=cnt[i-j];
	}
	if(rightsum==leftsum)	printf("Balanced\n");
	else printf("Not Balanced\n");

	return 0;
} 
```

代码稍显繁琐

*return用法：return （）？“ ”；“ ” ；
（）里是判断条件，满足条件返回第一个“”里的值，不满足返回第二个；*