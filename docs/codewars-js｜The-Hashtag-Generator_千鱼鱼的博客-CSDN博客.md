<!--yml
category: codewars
date: 2022-08-13 11:44:34
-->

# codewars js|The Hashtag Generator_千鱼鱼的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41435278/article/details/89359038?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-89359038.nonecase](https://blog.csdn.net/weixin_41435278/article/details/89359038?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-89359038.nonecase)

The marketing team is spending way too much time typing in hashtags.
Let's help them with out own Hashtag Generator!

Here's the deal:

*   It must start with a hashtag (`#`).
*   All words must have their first letter capitalized.
*   If the final result is longer than 140 chars it must return `false`.
*   If the input or the result is an empty string it must return `false`.

## Examples

```
" Hello there thanks for trying my Kata"  =>  "#HelloThereThanksForTryingMyKata"
"    Hello     World   "                  =>  "#HelloWorld"
""                                        =>  false
```

1、字符串中单词首字母大写

2、删除所有空格

我的代码：

```
function generateHashtag (str) {
  var hashtag=str.replace(/\b[a-z]/g,function(s){return s.toUpperCase()}).replace(/\s+/g,'');
  console.log(hashtag.length);
  if(hashtag=='') return false;
  else if(hashtag.length>=140) return false;
  else return '#'+hashtag;
}
```

大佬的：

```
function generateHashtag (str) {
  return str.length > 140 || str === '' ? false :
    '#' + str.split(' ').map(capitalize).join('');
}

function capitalize(str) {
  return str.charAt(0).toUpperCase() + str.slice(1);
}
```