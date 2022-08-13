<!--yml
category: codewars
date: 2022-08-13 11:41:54
-->

# Mexican Wave（C语言CodeWars）_coolsunxu的博客-CSDN博客_codewars c语言

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105715281?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-27-105715281-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/coolsunxu/article/details/105715281?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-27-105715281-null-null.142^v40^control,185^v2^control&utm_term=codewars)

解题思路：

（1）注意空格是不被考虑的

```
#include <ctype.h>
void wave(const char *y, char **target) {
    int count=0,counts=0;
    const char *p = y;
    while(*y!='\0') {
	if(!isspace(*y)) {
	    strcpy(target[count],p);
	    target[count][counts]=toupper(*y);
	    count++;
	}
	counts++,y++;
    }
}
```