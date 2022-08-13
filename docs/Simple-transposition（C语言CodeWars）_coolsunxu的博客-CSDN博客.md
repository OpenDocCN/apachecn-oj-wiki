<!--yml
category: codewars
date: 2022-08-13 11:49:25
-->

# Simple transposition（C语言CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105746024?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-105746024.nonecase](https://blog.csdn.net/coolsunxu/article/details/105746024?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-105746024.nonecase)

解题思路：

（1）使用下标的奇偶性

（2）将对应的字符赋值给对应的字符串，最后连接

```
#include <string.h>

char *simple_transposition(const char *s) {

    char *row1 = (char*)calloc(strlen(s)+1,sizeof(char));
    char *row2 = (char*)calloc(strlen(s)/2+1,sizeof(char));
    char *p=row1,*q=row2;
    int i = 0;
    while(*s) {
      if(i%2==0) *p=*s,p++;
      else *q=*s,q++;
      s++;
      i++;
    }
    return strcat(row1,row2);

}
```