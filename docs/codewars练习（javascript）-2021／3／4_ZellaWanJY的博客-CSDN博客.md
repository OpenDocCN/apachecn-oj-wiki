<!--yml
category: codewars
date: 2022-08-13 11:46:57
-->

# codewars练习（javascript）-2021/3/4_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/114358068?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-114358068.nonecase](https://blog.csdn.net/FemaleHacker/article/details/114358068?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-114358068.nonecase)

## codewars-js练习

### 2021/3/4

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Reversed Words】

Given number `n`, such that `n > 1`, find if its 2nd root, 4th root and 8th root are all integers (fractional part is `0`), return `true` if it exists, `false` if not.

**<mark>example</mark>**：

```
reverseWords("The greatest victory is that which requires no battle") 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function reverseWords(str){
            return (str.split(' ')).reverse().join(' ')
        }

        console.log(reverseWords("hello world!")); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>
开组会，些许有点偷懒…