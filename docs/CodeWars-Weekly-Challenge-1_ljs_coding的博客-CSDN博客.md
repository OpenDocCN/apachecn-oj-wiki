<!--yml
category: codewars
date: 2022-08-13 11:49:10
-->

# CodeWars Weekly Challenge 1_ljs_coding的博客-CSDN博客

> 来源：[https://blog.csdn.net/ChristineAS/article/details/86410426?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-86410426.nonecase](https://blog.csdn.net/ChristineAS/article/details/86410426?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-86410426.nonecase)

### Codewars Weekly Challenge 1

#### 1 问题描述

Create a function which answers the question “Are you playing banjo?”.If your name starts with the letter “R” or lower case “r”, you are playing banjo!The function takes a name as its only argument, and returns one of the following strings:
name + " plays banjo"
name + " does not play banjo"

```
function areYouPlayingBanjo(name) {
  if(name.substring(0,1)=='R'||name.subString(0,1)=='r'){
  	name+=" plays banjo";
  }else{
  	name+=" does not play banjo";
  }
  return name;
} 
```

```
function areYouPlayingBanjo(name) {
  return name + (name[0].toLowerCase() == 'r' ? ' plays' : ' does not play') + " banjo";
} 
```

#### 2 问题描述

Definition
A number is called Automorphic number if and only if its square ends in the same digits as the number itself.
Task
Given a number determine if it Automorphic or not .

```
function automorphic(n){
  var length1=n.toString().length;
  var length2=(n*n).toString().length;
  return (n*n).toString().substring(length2-length1,length2)==n.toString()?"Automorphic":"Not!!";
} 
```

```
const automorphic = n => String(n*n).endsWith(String(n)) ? "Automorphic" : "Not!!" ; 
```

#### 3 问题描述

Description:
Implement the method map, which accepts a linked list (head) and a mapping function, and returns a new linked list (head) where every element is the result of applying the given mapping method to each element of the original list.

Make sure you do not modify the original list!

For example: Given the list: 1 -> 2 -> 3, and the mapping function x => x * 2, map should return 2 -> 4 -> 6

The linked list is defined as follows:
function Node(data, next = null) {
this.data = data;
this.next = next;
}
Note: the list may be null and can hold any type of value.

```
function map(head, f) {
  return !head ? null : new Node(f(head.data), map(head.next, f));
} 
```

#### 4问题描述

Description:
Given the string representations of two integers, return the string representation of the sum of those integers.

For example:

sumStrings(‘1’,‘2’) // => ‘3’

```
function sumStrings(a,b) { 
  var res='',c=0;
  a=a.split('');
  b=b.split('');
  while(a.length||b.length||c){//pop() 方法用于删除并返回数组的最后一个元素
   c+=~~a.pop()+~~b.pop();
   res=c%10+res;
   c=c>9;//是否进位
  }
  return res.replace(/^0+/,'');//替代开头的多个0，比如sumStrings('00103', '08567') - Expected: '8670', instead got: '08670'
} 
```

#### 5 问题描述

A pangram is a sentence that contains every single letter of the alphabet at least once. For example, the sentence “The quick brown fox jumps over the lazy dog” is a pangram, because it uses the letters A-Z at least once (case is irrelevant).

Given a string, detect whether or not it is a pangram. Return True if it is, False if not. Ignore numbers and punctuation.

```
function isPangram(string){
  var character;
  var flag=0;
  for(i=0;i<26;i++){
     character=String.fromCharCode(65+i);
     if((string.indexOf(character.toLowerCase())==-1)&&(string.indexOf(character)==-1)){
        flag=1;
        break;
     }
  }
  return flag==0?true:false;
} 
```

```
function isPangram(string){
  string = string.toLowerCase();
  return "abcdefghijklmnopqrstuvwxyz".split("").every(function(x){
    return string.indexOf(x) !== -1;
  });
} 
```