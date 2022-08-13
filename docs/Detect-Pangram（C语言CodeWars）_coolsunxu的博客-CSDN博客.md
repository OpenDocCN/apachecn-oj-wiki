<!--yml
category: codewars
date: 2022-08-13 11:48:15
-->

# Detect Pangram（C语言CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105877509?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-105877509.nonecase](https://blog.csdn.net/coolsunxu/article/details/105877509?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-105877509.nonecase)

解题思路：

（1）创建一个hash table，其中key为字符的ascii值

（2）访问一个未访问的，计数加1，并设置其为已访问

（3）计数达到26则返回true退出，否则最后返回fasle

```
#include <ctype.h>
#include <stdlib.h>

#include <stdbool.h>

bool is_pangram(const char *str_in) {

    int* hash = (int*)calloc(256,sizeof(int));
    int count = 0;
    while(*str_in!='\0') {
    if(isalpha(*str_in)) {
      if(hash[tolower(*str_in)]==0) {
        hash[tolower(*str_in)]=1;
        count++;
        //printf("%c,%d\n",*str_in,count);
        if(count==26) return true;
      }
    }
    str_in++;
  }
  free(hash);hash=NULL;
  return false;
}
```