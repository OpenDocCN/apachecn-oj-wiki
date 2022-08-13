<!--yml
category: codewars
date: 2022-08-13 11:29:07
-->

# Codewars第三天--Create Phone Number_soufal的博客-CSDN博客

> 来源：[https://blog.csdn.net/u011562123/article/details/81157879?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-81157879.142^v40^control,185^v2^control](https://blog.csdn.net/u011562123/article/details/81157879?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-81157879.142^v40^control,185^v2^control)

Codewars第三天–Create Phone Number

Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.

Example:
create_phone_number([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]) # => returns “(123) 456-7890”
The returned format must be correct in order to complete this challenge.
Don’t forget the space after the closing parentheses!

```
def create_phone_number(n):

    return "({}{}{}) {}{}{}-{}{}{}{}".format(n[0],n[1],n[2],n[3],n[4],n[5],n[6],n[7],n[8],n[9]) 
```