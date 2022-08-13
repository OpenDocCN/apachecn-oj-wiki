<!--yml
category: codewars
date: 2022-08-13 11:48:33
-->

# codewars4 Credit Card Mask_z_y_ning的博客-CSDN博客

> 来源：[https://blog.csdn.net/z_y_ning/article/details/102509641?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-102509641.nonecase](https://blog.csdn.net/z_y_ning/article/details/102509641?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-102509641.nonecase)

**Instructions**

Usually when you buy something, you’re asked whether your credit card number, phone number or answer to your most secret question is still correct. However, since someone could look over your shoulder, you don’t want that shown on your screen. Instead, we mask it.

Your task is to write a function maskify, which changes all but the last four characters into ‘#’.
**Examples**
maskify(“4556364607935616”) == “############5616”
maskify( “64607935616”) == “#######5616”
maskify( “1”) == “1”
maskify( “”) == “”

#“What was the name of your first pet?”
maskify(“Skippy”) == “##ippy”
maskify(“Nananananananananananananananana Batman!”) == “####################################man!”
**Solution:**

```
def maskify(cc):
    return "#"*(len(cc)-4) + cc[-4:] 
```