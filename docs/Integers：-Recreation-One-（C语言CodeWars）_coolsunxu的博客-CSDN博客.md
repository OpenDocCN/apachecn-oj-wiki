<!--yml
category: codewars
date: 2022-08-13 11:44:47
-->

# Integers: Recreation One （C语言CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105705379?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-105705379.nonecase](https://blog.csdn.net/coolsunxu/article/details/105705379?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-105705379.nonecase)

解题思路：

（1）解法很暴力

（2）就是指针不太熟悉，容易出错，哈哈哈

```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

typedef struct Pair Pair;
struct Pair {
    long long first;
    long long snd;
};
// fill length with the number of pairs in your array of pairs
Pair** listSquared(long long m, long long n, int* length) {
    // your code
    Pair **p = (Pair**)calloc(0,sizeof(Pair*));
    int count = 0;
    long long sum = 0,temp;
    for(long long i = m;i<=n;i++) {
	sum=0;
	for(long long j=1;j<=i;j++) {
	    if (i%j==0) sum+=j*j;
	}
	temp = sqrt(sum);
	if (temp*temp==sum) {
            p = (Pair**)realloc(p,(count+1)*sizeof(Pair*));
	    Pair* s = (Pair*)calloc(1, sizeof(Pair));
	    s->first = i;
	    s->snd = sum;
	    p[count++] = s;
	}
    }
    *length=count;
    return p;
}
```