<!--yml
category: codewars
date: 2022-08-13 11:44:07
-->

# codewars 6kyu Valid Braces_小嬴布菱的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_29549685/article/details/117387622?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-117387622.nonecase](https://blog.csdn.net/qq_29549685/article/details/117387622?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-117387622.nonecase)

codewars [6kyu Valid Braces](https://www.codewars.com/kata/5277c8a221e209d3f6000b56/train/javascript)

题目大意：给定一个由括号组成的字符串，判断这个字符串中的括号是否匹配。

> 给几个例子：
> ‘()’ >>true
> ‘({)}’ >> flase
> ‘{[()]}’ >>true

首先想到堆栈！用到了今天刚刚学到的 for of

```
function validBraces(braces) {

  var temp = [];
  for (ch of braces) {
    if (ch == "(" || ch == "[" || ch == "{") {
      temp.push(ch);
    } else if (ch == ")") {
      let a = temp.pop();
      if (a != "(") {
        temp.push(a);
        temp.push(ch);
      }
    } else if (ch == "]") {
      let a = temp.pop();
      if (a != "[") {
        temp.push(a);
        temp.push(ch);
      }
    } else if (ch == "}") {
      let a = temp.pop();
      if (a != "{") {
        temp.push(a);
        temp.push(ch);
      }
    }
    console.log(ch, temp);
  }
  if (temp.length == 0) {
    return true;
  } else {
    return false;
  }
} 
```

最后的判断 if 的 5 行代码可以修改为一行：

```
return temp.length === 0; 
```

看了别人的 solution，有个解法十分巧妙，运用到了字典进行括号的匹配判断，也同时运用堆栈

```
function validBraces(braces) {
  var matches = { "(": ")", "{": "}", "[": "]" };
  var stack = [];
  var currentChar;

  for (var i = 0; i < braces.length; i++) {
    currentChar = braces[i];

    if (matches[currentChar]) {

      stack.push(currentChar);
    } else {

      if (currentChar !== matches[stack.pop()]) {
        return false;
      }
    }
  }

  return stack.length === 0; 
} 
```

当然还有使用正则表达式的 sulution

```
function validBraces(braces) {
  while (/\(\)|\[\]|\{\}/g.test(braces)) {
    braces = braces.replace(/\(\)|\[\]|\{\}/g, "");
  }
  return !braces.length;
} 
```

也可以用switch case解，也是用堆栈。

```
function validBraces(braces){
  for (var i = 0, depth = []; i < braces.length; i++) {
    switch (braces[i]) {
      case '(': case '[': case '{': depth.push(braces[i]); break;
      case ')': if (depth.pop() != '(') return false; break;
      case ']': if (depth.pop() != '[') return false; break;
      case '}': if (depth.pop() != '{') return false; break;
    }
  }
  return depth.length == 0;
} 
```