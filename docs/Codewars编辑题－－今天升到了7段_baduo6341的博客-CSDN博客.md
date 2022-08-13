<!--yml
category: codewars
date: 2022-08-13 11:44:28
-->

# Codewars编辑题－－今天升到了7段_baduo6341的博客-CSDN博客

> 来源：[https://blog.csdn.net/baduo6341/article/details/101476968?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-101476968.nonecase](https://blog.csdn.net/baduo6341/article/details/101476968?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-101476968.nonecase)

今天做的题目是：**写一个函数toWeirdCase()，对给定的一个字符串string进行偶数位（包括0）变成大写的操作**，字符串string分为单个单词的字符串和多个单词组成的句子。效果应该是这个样子滴：

*我是这样写的*，写完很有成就感啊，觉得我是最牛逼的，我太厉害了...balabala...：

```
 1 function toWeirdCase(string){ 2     //先判断字符串是否是单个单词组成
 3     if(string.indexOf(" ")==-1){//单个单词组成的字符串
 4        var arr1=string.split("");
 5        for(var i=0;i<arr1.length;i++){
 6             //偶数位的字母变成大写
 7            if(i%2==0){
 8                arr1[i]=arr1[i].toUpperCase();
 9            }else{ 10                continue; 11 } 12 } 13        return  arr1.join(""); 14     }else{//多个单词组成的字符串，中间有空格
15          var str2 = ""; 16          //把字符串由空格分割成数组
17          var arr2 = string.split(' '); 18          var arr3 = []; 19          for(var j=0;j<arr2.length;j++){ 20             //把arr2的每一项分割成数组，进行操作
21              arr3 = arr2[j].split(""); 22              for(var k=0;k<arr3.length;k++){ 23                 if(k%2==0){ 24                    arr3[k]=arr3[k].toUpperCase(); 25                 }else{ 26                    continue; 27 } 28 } 29             //str2是arr2的某一项
30              str2=arr3.join(""); 31              arr2[j]=str2; 32 } 33          return arr2.join(" "); 34 } 35 }     
```

其实我本来用的不是数组，而是直接用字符串的replace（）进行操作的。在这里出现了问题，replace方法的第一个参数可以是字符串也可以是正则表达式，是匹配的；第二个参数可以是字符串也可以是函数，是替换的（字符串／操作）。在我使用的时候替换操作是这样写的：

```
(部分代码，足够表达）
1       var str1=string;
2       for(var i=0;i<string.length;i++){
3         if(i%2==0){
4             str1=str1.replace(str1.charAt(i),str1.charAt(i).toUpperCase());//在这里str1.charAt(i)是一个字符，会匹配字符串中此字符出现的第一个位置，当一个字符串中有多个此字符时就会出现错误。
5          }else{
6             continue;
7          }
8       }
9 return str1; 
```

我看了别人写的代码，瞬间泪奔啊有木有,瞬间觉得被神灵抛弃，我是最搓的那一个...哭＝.＝.

看这个：

```
1 function toWeirdCase(string){ 2   return string.split(' ').map(function(word){ 3     return word.split('').map(function(letter, index){ 4       return index % 2 == 0 ? letter.toUpperCase() : letter.toLowerCase() 5     }).join(''); 6   }).join(' '); 7 }
```

看这个：

```
function toWeirdCaseCharacter(chr, index)
{ return index % 2 ? chr.toLowerCase() : chr.toUpperCase();
} function toWeirdCaseWord(word){ return word.split("").map(toWeirdCaseCharacter).join("");
} function toWeirdCase(string){ return string.split(" ").map(toWeirdCaseWord).join(" ");
}
```

再看这个：

```
function toWeirdCase(string){ return string.replace(/(\w{1,2})/g,(m)=>m[0].toUpperCase()+m.slice(1))
}
```

我实在是没力气了，放下网址吧：https://www.codewars.com/kata/weird-string-case/solutions/javascript/all/best_practice

这是我的第一篇博客，用于学习和交流，如果有**侵权**的地方和**错误**的地方，请联系小弟，我会立马修改，请不要报警...wuwawuwa.