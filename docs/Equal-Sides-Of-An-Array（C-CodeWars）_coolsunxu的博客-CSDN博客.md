<!--yml
category: codewars
date: 2022-08-13 11:51:42
-->

# Equal Sides Of An Array（C CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105659054?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-105659054.nonecase](https://blog.csdn.net/coolsunxu/article/details/105659054?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-105659054.nonecase)

解题思路：

（1）dp[i]记录values从起始位置0到当前位置[i]的和

（2）再重新遍历，寻找满足公式的下标

```
int find_even_index(const int *values, int length) {

	int *dp = calloc(length,sizeof(int));
	int sum = 0;

	for(int i=0;i<length;i++) {
		sum+=values[i];
		dp[i] = sum;
	}
	for(int i=0;i<length;i++) {
		if (dp[i]-values[i]==dp[length-1]-dp[i]) return i;
	}
	return -1;
}
```