<!--yml
category: codewars
date: 2022-08-13 11:51:35
-->

# Who likes it?（C语言CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105589187?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-105589187.nonecase](https://blog.csdn.net/coolsunxu/article/details/105589187?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-105589187.nonecase)

参考网址：[https://www.codewars.com/kata/5266876b8f4bf2da9b000362/solutions/c](https://www.codewars.com/kata/5266876b8f4bf2da9b000362/solutions/c)

（1）使用asprintf，asprintf()可以说是一个增强版的sprintf()

（2）在不确定字符串的长度时，能够根据格式化的字符串长度，申请足够的内存空间。

```
char* likes(size_t n, const char *const names[n]) {
  char *buf;
  switch (n) {
    case 0:  { asprintf(&buf, "no one likes this"); break; }
    case 1:  { asprintf(&buf, "%s likes this", names[0]); break; }
    case 2:  { asprintf(&buf, "%s and %s like this", names[0], names[1]); break; }
    case 3:  { asprintf(&buf, "%s, %s and %s like this", names[0], names[1], names[2]); break; }
    default: { asprintf(&buf, "%s, %s and %d others like this", names[0], names[1], n-2); break; }
  }
  return buf;
}
```

（3）使用sprintf

```
char* likes(size_t n, const char *const names[n]) {

    char * ret, * count_as_str;
    switch(n) {
        case 0:
            return strdup("no one likes this");
        case 1:
            ret = calloc(12 + strlen(names[0]), sizeof(char));
            sprintf(ret, "%s likes this", names[0]);
            return ret;
        case 2:
            ret = calloc(16 + strlen(names[0]) + strlen(names[1]), sizeof(char));
            sprintf(ret, "%s and %s like this", names[0], names[1]);
            return ret;
        case 3:
            ret = calloc(18 + strlen(names[0]) + strlen(names[1]) + strlen(names[2]), sizeof(char));
            sprintf(ret, "%s, %s and %s like this", names[0], names[1], names[2]);
            return ret;
        default:
            asprintf(&count_as_str, "%d", n-2);
            ret = calloc(25 + strlen(names[0]) + strlen(names[1]) + strlen(count_as_str), sizeof(char));
            sprintf(ret, "%s, %s and %s others like this", names[0], names[1], count_as_str);
            return ret;
    }
}
```