<!--yml
category: codewars
date: 2022-08-13 11:38:33
-->

# 【Codewars】＜6kyu＞Detect Pangram_cbat01的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_36270908/article/details/111864909?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-111864909-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_36270908/article/details/111864909?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-111864909-null-null.142^v40^control,185^v2^control&utm_term=codewars)

### 一、题目

> A pangram is a sentence that contains every single letter of the alphabet at least once. For example, the sentence “The quick brown fox jumps over the lazy dog” is a pangram, because it uses the letters A-Z at least once (case is irrelevant).
> Given a string, detect whether or not it is a pangram. Return True if it is, False if not. Ignore numbers and punctuation.
> 
> 这道题要我们实现的是，判断字符串中是否包含·`a-z`至少一次（不区分大小写），是的话返回`true`，否则返回`false`

### 二、例子

```
var string = "The quick brown fox jumps over the lazy dog."
isPangram(string) 
var string = "This is not a pangram."
isPangram(string) 
```

### 三、题解一

```
 function isPangram(string){
    for(let i = 65; i <= 90; i++){
        if(string.toUpperCase().indexOf(String.fromCharCode(i)) == -1){
            return false;
        }
    }
    return true;
} 
```

### 四、题解二

```
 function isPangram(string){
    string = string.toLowerCase();
    return "abcdefghijklmnopqrstuvwxyz".split("").every(function(x){
        return string.indexOf(x) !== -1;
    });
} 
```