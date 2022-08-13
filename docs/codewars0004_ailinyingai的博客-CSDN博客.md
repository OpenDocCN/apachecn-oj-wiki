<!--yml
category: codewars
date: 2022-08-13 11:45:02
-->

# codewars0004_ailinyingai的博客-CSDN博客

> 来源：[https://blog.csdn.net/ailinyingai/article/details/102914390?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-102914390.nonecase](https://blog.csdn.net/ailinyingai/article/details/102914390?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-102914390.nonecase)

```
# https://www.codewars.com/kata/coordinates-validator
import re
def is_valid_coordinates(coordinates):
    pattern = re.compile(r'^(-)?\d+(\.\d+)?,(\s)?(-)?\d+(\.\d+)?$')

    if pattern.match(coordinates):
        pieces = [abs(float(item)) for item in coordinates.split(",")]
        return pieces[0] <= 90 and pieces[1] <= 180
    return False 
```