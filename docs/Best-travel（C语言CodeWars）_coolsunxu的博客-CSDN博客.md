<!--yml
category: codewars
date: 2022-08-13 11:43:04
-->

# Best travel（C语言CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105730473?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-105730473.nonecase](https://blog.csdn.net/coolsunxu/article/details/105730473?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-105730473.nonecase)

解题思路：

（1）使用组合来求所需要的数组

```
#include <stdlib.h>
void combination(int *max, int t, int p[], int k, int ls[], int szls, int begin, int index) {
	if(k==0) {
	    int sum = 0;
	    for(int i=0;i<index;i++) {
		sum+=p[i];
	    }
	    if(*max<sum && sum<=t) *max=sum;
	}

	for(int i=begin;i<szls;i++) {
		p[index]=ls[i];
		combination(max,t,p,k-1,ls,szls,i+1,index+1);
	}
}

int chooseBestSum(int t, int k, int ls[], int szls) {
    if (k>szls||k<=0) return -1;
    int max = -1;
    int *p = (int*)calloc(szls,sizeof(int));
    combination(&max,t,p,k,ls,szls,0,0);
    free(p);
    p=NULL;
    return max;
} 
```