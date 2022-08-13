<!--yml
category: codewars
date: 2022-08-13 11:51:04
-->

# Product of consecutive Fib numbers（C语言CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105894819?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-105894819.nonecase](https://blog.csdn.net/coolsunxu/article/details/105894819?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-105894819.nonecase)

解题思路：

（1）两个指针，指向当前F数列的值和前一个值，依次交替前进

```
typedef unsigned long long ull;

unsigned long long* productFib(ull prod) {
  ull a=0,b=1,c;
  ull *v = (ull*)calloc(3,sizeof(ull));
  while(a*b<prod) {
    c = a+b;
    a = b;
    b = c;
  }
  v[0]=a;
  v[1]=b;
  if(a*b==prod) v[2]=1;
  else v[2]=0;
  return v;
} 
```