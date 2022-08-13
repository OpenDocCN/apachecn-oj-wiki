<!--yml
category: codewars
date: 2022-08-13 11:39:08
-->

# codewars 5kyu Simple Pig Latin_小嬴布菱的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_29549685/article/details/117400242?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-17-117400242-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_29549685/article/details/117400242?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-17-117400242-null-null.142^v40^control,185^v2^control&utm_term=codewars)

codewars [5kyu Simple Pig Latin](https://www.codewars.com/kata/520b9d2ad5c005041100000f/train/javascript)

题目大意：把每个单词的第一个字母移到该单词的末尾，最后在单词末尾加上 ay，输出字符串。标点符号不进行处理。

我的思路是先把每个单词以空格为分割存到一个列表里，对列表里每个单词进行处理，如果该词是标点符号，不做处理，否则就把该词的第一个字母移到该词的末尾，最后在单词末尾加上 ay 和空格，如果是最后一个单词，末尾不加空格。

```
function pigIt(str) {

  var temp = str.split(" ");
  var ans = "";
  for (let i = 0; i < temp.length; i++) {
    if (
      temp[i].charCodeAt() < 65 ||
      (temp[i].charCodeAt() > 90 && temp[i].charCodeAt() < 97) ||
      temp[i].charCodeAt() > 122
    ) {
    } else {
      temp[i] = temp[i].slice(1, temp[i].length) + temp[i][0] + "ay";
    }

    if (i != temp.length - 1) {
      ans += temp[i] + " ";
    } else {
      ans += temp[i];
    }
  }
  return ans;
} 
```

中间也想到用正则表达式，但是正则还不大会用。

```
function pigIt(str) {
  return str.replace(/(\w)(\w*)(\s|$)/g, "$2$1ay$3");
}
const pigIt = (s) => s.replace(/(\w)(\w*)/g, "$2$1ay"); 
```

```
function pigIt(str) {
  return str.replace(/\w+/g, (w) => {
    return w.slice(1) + w[0] + "ay";
  });
} 
```

```
function pigIt(str) {
  var arrayWord = str.split(" ");
  return arrayWord
    .map(function (word) {
      var firstLetter = word.charAt(0);
      return word.slice(1) + firstLetter + "ay";
    })
    .join(" ");
}
function pigIt(str) {
  return str
    .split(" ")
    .map((item) => `${item.substr(1)}${item[0]}ay`)
    .join(" ");
} 
```

也有这样条理清晰代码行数比我多的大佬~

```
function pigIt(str) {
  let newStr = "";
  const array = str.split(" ");
  for (let i of array) {
    let firstLetter = ""; 
    for (let j in i) {
      if (j === "0") {
        firstLetter += i[j]; 
      } else {
        newStr += i[j];
      }
    }
    newStr += firstLetter; 
    newStr += " "; 
  }
  newArray = newStr.split(" ");
  newArray.pop(); 
  let result = ""; 
  for (let index of newArray) {
    if (index.length != 1) {
      result += index;
      result += "ay";
      result += " ";
    } else if (index.length == 1) {
      if (index == "?" || index == "!" || index == ".") {

        result += index;
      } else {
        result += index;
        result += "ay";
        result += " ";
      }
    }
  }

  if (result[result.length - 1] === " ") {

    result = result.slice(0, result.length - 1);
  }
  return result;
} 
```