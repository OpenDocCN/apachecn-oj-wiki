<!--yml
category: codewars
date: 2022-08-13 11:47:12
-->

# Shortest Word（C语言CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105551039?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-105551039.nonecase](https://blog.csdn.net/coolsunxu/article/details/105551039?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-105551039.nonecase)

解题思路：将空格作为分隔符

```
ssize_t find_short(const char *s) {
	ssize_t min = INT_MAX,count = 0;
	while(*s!='\0') {
		if (*s!=' ') {
			count = 0;
			while(*s!=' ' && *s!='\0') {
				count++;
				s++;
			}
			if (min>count) min = count;
		} else s++;
	}
    return min;
}
```