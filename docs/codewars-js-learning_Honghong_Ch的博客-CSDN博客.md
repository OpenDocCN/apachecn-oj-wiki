<!--yml
category: codewars
date: 2022-08-13 11:39:19
-->

# codewars js learning_Honghong_Ch的博客-CSDN博客

> 来源：[https://blog.csdn.net/CherryChanccc/article/details/117409046?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-22-117409046-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/CherryChanccc/article/details/117409046?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-22-117409046-null-null.142^v40^control,185^v2^control&utm_term=codewars)

1.Abbreviate a Two Word Name

```
function abbrevName(name){

  var nameArray = name.split(" ");
  return (nameArray[0][0] + "." + nameArray[1][0]).toUpperCase();
}
```

2.获取字符串的长度（牛客网）

```
function strLength(s, bUnicode255For1) {
    var l = s.length;
    if(!bUnicode255For1){
        for(var i in s){
            if(s.charCodeAt(i)>255){
                l++;
            }
        }
    }
    return l;
}
```

3.邮箱字符串判断（牛客网）

```
function isAvailableEmail(sEmail) {
   var reg=/^([0-9A-Za-z\-_\.]+)@([0-9a-z]+\.[a-z]{2,3}(\.[a-z]{2})?)$/g;
   return reg.test(sEmail)
}
```