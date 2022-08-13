<!--yml
category: codewars
date: 2022-08-13 11:52:13
-->

# codewars js|Count the number of Duplicates 计算重复的字母数量_千鱼鱼的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41435278/article/details/89357628?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-89357628.nonecase](https://blog.csdn.net/weixin_41435278/article/details/89357628?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-89357628.nonecase)

Write a function that will return the count of **distinct case-insensitive** alphabetic characters and numeric digits that occur more than once in the input string. The input string can be assumed to contain only alphabets (both uppercase and lowercase) and numeric digits.

### Example

"abcde" -> 0 `# no characters repeats more than once`
"aabbcde" -> 2 `# 'a' and 'b'`
"aabBcde" -> 2 `# 'a' occurs twice and 'b' twice (`b` and `B`)`
"indivisibility" -> 1 `# 'i' occurs six times`
"Indivisibilities" -> 2 `# 'i' occurs seven times and 's' occurs twice`
"aA11" -> 2 `# 'a' and '1'`
"ABBA" -> 2 `# 'A' and 'B' each occur twice`

`给定一个字符串比如说是 aabbcaAb，忽略大小写，a和b重复，返回2，返回的是重复的字母个数，而不是重复次数`

`对于 aabbcaAb，`

`1、先把所有字母变成小写，toLowerCase()(string对象的属性)`

`2、把字符串转成数组并且按照字典顺序排序，.split().sort()，['a','a','a','a','b','b','b','c']`

`3、把得到的数组组合成字符串，join(''),'aaaabbbc'`

`4、用正则表达式匹配重复字母 返回 ['aaaa','bbb','c']`

5、返回以上数组长度

我的代码：

```
function duplicateCount(text){
  //...
  var str = text.toLowerCase().split('').sort().join('');
  var arr= str.match(/(.)\1+/g);
  console.log(arr);
  if(arr==null) return 0;
  else return arr.length; 
}
```

大佬的代码：

```
function duplicateCount(text){
  return (text.toLowerCase().split('').sort().join('').match(/([^])\1+/g) || []).length;
}
```