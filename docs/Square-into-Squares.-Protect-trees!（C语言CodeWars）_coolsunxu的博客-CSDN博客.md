<!--yml
category: codewars
date: 2022-08-13 11:43:50
-->

# Square into Squares. Protect trees!（C语言CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105723782?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-105723782.nonecase](https://blog.csdn.net/coolsunxu/article/details/105723782?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-105723782.nonecase)

解题思路：

（1）因为没有通过全部测试，因此这里仅仅讲一下怎么讲整数数组变为字符串

（2）使用asprintf,realloc

```
char *num2string(long long *numbers,int count) { //数组以及个数
    char *p = (char*)calloc(1,sizeof(char));
    p[0]='[';
    if(count>=0) {
    char *buf;
    int len=1;
    for(int i=0;i<count-1;i++) {
        asprintf(&buf,"%lld,",numbers[i]);
	len+=strlen(buf);
	p = (char*)realloc(p,len*sizeof(char));
	strcat(p,buf);
    }
    asprintf(&buf,"%lld]",numbers[count-1]);
    len+=strlen(buf);
    p = (char*)realloc(p,len*sizeof(char));
    strcat(p,buf);
    //printf("%s",p);
    } else {
        p = (char*)realloc(p,2*sizeof(char));
	strcat(p,"]");
    }
    return p;
}
```

（3）使用sprintf，realloc

```
char *num2string(long long *numbers,int count) { //数组以及个数
    char *p = (char*)calloc(1,sizeof(char));
    p[0]='[';
    if(count>0) {
        char buf[50];
	int len=1;
	for(int i=0;i<count-1;i++) {
	    sprintf(buf,"%lld,",numbers[i]);
	    len+=strlen(buf);
	    p = (char*)realloc(p,len*sizeof(char));
	    strcat(p,buf);
	}
	sprintf(buf,"%lld]",numbers[count-1]);
	len+=strlen(buf);
	p = (char*)realloc(p,len*sizeof(char));
	strcat(p,buf);
	//printf("%s",p);
    } else {
	p = (char*)realloc(p,2*sizeof(char));
	strcat(p,"]");
    }
    return p;
}
```

（4）只使用sprintf

```
char *num2string(long long *numbers,int count) { //数组以及个数
    char *p = (char*)calloc(20,sizeof(char));
    p[0]='[';
    if(count>0) {
    char buf[50];
        for(int i=0;i<count-1;i++) {
	    sprintf(buf,"%lld,",numbers[i]);
	    strcat(p,buf);
	}
	sprintf(buf,"%lld]",numbers[count-1]);
	strcat(p,buf);
	//printf("%s",p);
    } else {
	strcat(p,"]");
    }
    return p;
}
```

（5）参考别人的递归，但是没有通过所有的测试，关键打印出来最后是哪个出错，尴尬。。。

```
int divide(long long *numbers, long long remain, long long last, int *count) {
    if (remain <= 0) {
        if (remain == 0) return 1; else return 0;
    }
    for (long long i = last - 1; i > 0; i--) {
        if (divide(numbers, remain - (i * i), i,count) == 1 ) {
            numbers[*count] = i;
            *count = *count +1;
            return 1;
        }
    }
    return 0;
}

char *num2string(long long *numbers,int count) { //数组以及个数
    char *p = (char*)calloc(20,sizeof(char));
    p[0]='[';
    if(count>0) {
    char buf[50];
        for(int i=0;i<count-1;i++) {
	    sprintf(buf,"%lld,",numbers[i]);
	    strcat(p,buf);
	}
	sprintf(buf,"%lld]",numbers[count-1]);
	strcat(p,buf);
	//printf("%s",p);
    } else {
	strcat(p,"]");
    }
    return p;
}

char* decompose(long long n) {
    long long a[100];
    int count = 0;
    printf("%lld",n);
    divide(a, n * n, n,&count);
    char *p = num2string(a,count);
    return p;
}
```