<!--yml
category: codewars
date: 2022-08-13 11:45:46
-->

# Codewars: Find the missing letter_咋回事,小老弟的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_42705075/article/details/81348274?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-81348274.nonecase](https://blog.csdn.net/weixin_42705075/article/details/81348274?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-81348274.nonecase)

```
def find_missing_letter(chars):
    for i in range(len(chars)):
        if not ord(chars[i]) + 1 == ord(chars[i+1]):
            return chr(ord(chars[i]) + 1)

chars = ['O','Q','R','S']
print(find_missing_letter(chars))
```