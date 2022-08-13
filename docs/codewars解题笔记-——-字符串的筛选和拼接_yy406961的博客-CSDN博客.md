<!--yml
category: codewars
date: 2022-08-13 11:38:51
-->

# codewars解题笔记 —— 字符串的筛选和拼接_yy406961的博客-CSDN博客

> 来源：[https://blog.csdn.net/yy406961/article/details/78107148?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-78107148.142^v40^control,185^v2^control](https://blog.csdn.net/yy406961/article/details/78107148?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-78107148.142^v40^control,185^v2^control)

题目：

Your job is to write a function which increments a string, to create a new string. If the string already ends with a number, the number should be incremented by 1\. If the string does not end with a number the number 1 should be appended to the new string.

Examples:
foo -> foo1
foobar23 -> foobar24
foo0042 -> foo0043
foo9 -> foo10
foo099 -> foo100

将字符串后面的数字加1，得到新的字符串。若字符串后面没数字，则补1。

我的答案：

```
function incrementString (strng) {
  if (!strng.match(/\d+$/)){
    return strng + '1'
  } else {
     return strng.replace(/\d+$/,v => {
            let n = v.length
            let a = (parseInt(v) + 1).toString().length
            if (n>a) {
              return new Array(n - a + 1).join('0') + (parseInt(v) + 1)
            } else {
              return parseInt(v) + 1
            }
         })
  }

}
```

票数最高的答案

ex：incrementString("abcd00999")

```
function incrementString(input) {
  if(isNaN(parseInt(input[input.length - 1]))) return input + '1';
  return input.replace(/(0*)([0-9]+$)/, function(match, p1, p2) {
    console.log('match is ' + match)  // 00999
    console.log('p1 is ' + p1)        // 00
    console.log('p2 is ' + p2)        // 999
    var up = parseInt(p2) + 1;
    return up.toString().length > p2.length ? p1.slice(0, -1) + up : p1 + up;
  });
}
```

思考：

1、题目有两个坑，第一，当字符串末尾没有数字的时候，给补个1。这一步我觉得我处理得比较简单

```
if (!strng.match(/\d+$/)){
    return strng + '1'
  } 
```

   **正则  /\d+$/**  => 匹配结尾的所有的数字

\d  =>   匹配一个字数字符，/\d/ = /[0-9]/ 

        +   =>   匹配前一项1次或者多次，至少一次

        $   =>   匹配的是字符的结尾,在多行检索中,匹配的是一行的结尾 

   **str.match(正则)** =>  match没有找到要求的字符时，返回NAN，直接判断是否为NAN即可。

2、当尾数为9时，往前进一位。而且数字前面的 0 不能丢，这个过程想了很久，没有想过可以将前面的 0 和后面的数字拆开。别人的代码就是利用这点操作的。

3、学到生成字符串 0 的方法

**new Array(****5).join('0')  =>   '0000' **

4、来研究下别人的代码

    ex：incrementString("abcd00999")

```
return input.replace(/(0*)([0-9]+$)/, function(match, p1, p2) {
    console.log('match is ' + match)  // 00999
    console.log('p1 is ' + p1)        // 00
    console.log('p2 is ' + p2)        // 999
    var up = parseInt(p2) + 1;
    return up.toString().length > p2.length ? p1.slice(0, -1) + up : p1 + up;
  });
```

replace的回调函数中，match是字符串中正则匹配到的值，p1对应的是正则中第一个圆括号里的表达式匹配到的值，p2对应的是正则中第二个圆括号里的表达式匹配到的值。将p2的值转为整数再 + 1，再将相加得到的结果转为字符串，拿到他的长度，如果他的长度大于相加之前的p2的长度，说明p2的数字全是9，例如 99 => 100，则需要将p1拿到的0减去一个，即 p1.slice(0, -1)。不然将p1和加好的数据拼接好就OK了。

**p1.slice(0, -1)** =>  选取从0开始到最后一个元素前的所有字符

## 定义和用法

slice() 方法可从已有的数组中返回选定的元素。

### 语法

```
arrayObject.slice(start,end)
```

| 参数 | 描述 |
| start | 必需。规定从何处开始选取。如果是负数，那么它规定从数组尾部开始算起的位置。也就是说，-1 指最后一个元素，-2 指倒数第二个元素，以此类推。 |
| end | 可选。规定从何处结束选取。该参数是数组片断结束处的数组下标。如果没有指定该参数，那么切分的数组包含从 start 到数组结束的所有元素。如果这个参数是负数，那么它规定的是从数组尾部开始算起的元素。 |

### 返回值

返回一个新的数组，包含从 start 到 end （不包括该元素）的 arrayObject 中的元素。

### 说明

请注意，该方法并不会修改数组，而是返回一个子数组。如果想删除数组中的一段元素，应该使用方法 Array.splice()。