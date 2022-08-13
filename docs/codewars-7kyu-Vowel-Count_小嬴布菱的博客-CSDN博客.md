<!--yml
category: codewars
date: 2022-08-13 11:41:02
-->

# codewars 7kyu Vowel Count_小嬴布菱的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_29549685/article/details/117339460?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-4-117339460-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_29549685/article/details/117339460?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-4-117339460-null-null.142^v40^control,185^v2^control&utm_term=codewars)

codewars [7kyu Vowel Count](https://www.codewars.com/kata/54ff3102c1bad923760001f3/train/javascript)

这个题的意思是，给一个字符串，计算字符串中元音字母（ aeiou ）的个数，输入只包括小写字母和空格。

我写的：

```
function getCount(str) {
  var vowelsCount = 0;

  for (let i = 0; i < str.length; i++) {
    if (
      str[i] == "a" ||
      str[i] == "e" ||
      str[i] == "i" ||
      str[i] == "o" ||
      str[i] == "u"
    ) {
      vowelsCount++;
    }
  }
  return vowelsCount;
} 
```

看看大佬们一行结束的代码：没错，大佬们一行就够了。

```
function getCount(str) {
  return (str.match(/[aeiou]/gi) || []).length;
}

function getCount(str) {
  return str.replace(/[^aeiou]/gi, "").length;
}

function getCount(str) {
  return str.split("").filter((c) => "aeiouAEIOU".includes(c)).length;
}

const getCount = (str) => str.replace(/[^aeiou]/g, "").length; 
```