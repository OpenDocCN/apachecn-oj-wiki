<!--yml
category: codewars
date: 2022-08-13 11:41:40
-->

# CodeWars上的JavaScript技巧积累_weixin_30375427的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_30375427/article/details/96874265?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-19-96874265-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_30375427/article/details/96874265?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-19-96874265-null-null.142^v40^control,185^v2^control&utm_term=codewars)

The `**slice()**` method returns a shallow copy of a portion of an array into a new array object selected from `begin` to `end` (`end` not included). The original array will not be modified.

```
var animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2)); // expected output: Array ["camel", "duck", "elephant"]
 console.log(animals.slice(2, 4)); // expected output: Array ["camel", "duck"]
 console.log(animals.slice(1, 5)); // expected output: Array ["bison", "camel", "duck", "elephant"]
```

对字符串进行操作的时候，slice(-1)是取最后一位字符。

[https://www.codewars.com/kata/56f695399400f5d9ef000af5/solutions/javascript](https://www.codewars.com/kata/56f695399400f5d9ef000af5/solutions/javascript) 

const correctTail = (body, tail) => body.slice(-1) === tail

The `**map()**` method creates a new array with the results of calling a provided function on every element in the calling array.

```
var array1 = [1, 4, 9, 16]; // pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1); // expected output: Array [2, 8, 18, 32]
```

The `**reduce()**` method executes a **reducer** function (that you provide) on each member of the array resulting in a single output value.

在使用这个的时候，需要注意的是，必须先自己封装一个reducer函数，然后传递给reduce方法

```
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue; // 1 + 2 + 3 + 4
console.log(array1.reduce(reducer)); // expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5)); // expected output: 15
```

The **reducer** function takes four arguments:

1.  Accumulator (acc)
2.  Current Value (cur)
3.  Current Index (idx)
4.  Source Array (src)

Your **reducer** function's returned value is assigned to the accumulator, whose value is remembered across each iteration throughout the array and ultimately becomes the final, single resulting value.

The `**reverse()**` method reverses an array *[in place](https://en.wikipedia.org/wiki/In-place_algorithm)*. The first array element becomes the last, and the last array element becomes the first.

```
var array1 = ['one', 'two', 'three'];
console.log('array1: ', array1); // expected output: Array ['one', 'two', 'three']

var reversed = array1.reverse(); 
console.log('reversed: ', reversed); // expected output: Array ['three', 'two', 'one']

/* Careful: reverse is destructive. It also changes
the original array */ console.log('array1: ', array1); // expected output: Array ['three', 'two', 'one']
```

The **`replace()`** method returns a new string with some or all matches of a `pattern` replaced by a `replacement`. The `pattern` can be a string or a [`RegExp`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp "The RegExp constructor creates a regular expression object for matching text with a pattern."), and the `replacement` can be a string or a function to be called for each match. If `pattern` is a string, only the first occurrence will be replaced.

The original string is left unchanged.

### 答案1

It isn't required, but by default `string.replace` in JavaScript will **only replace the first matching value** it finds. Adding the `/g` will mean that all of the matching values are replaced.

### 答案2

The "**g**" that you are talking about at the end of your regular expression is called a "modifier". The "**g**" represents the "**global modifier**". This means that your replace will replace all copies of the matched string with the replacement string you provide.

A list of useful modifiers:

1.  **g** - Global replace. Replace all instances of the matched string in the provided text.
2.  **i** - Case insensitive replace. Replace all instances of the matched string, ignoring differences in case.
3.  **m** - Multi-line replace. The regular expression should be tested for matches over multiple lines.

You can combine modifiers, such as g and i together, to get a global case insensitive search.

Examples:

```
//Replace the first lowercase t we find with X 'This is sparta!'.replace(/t/,'X'); //result: 'This is sparXa!' //Replace the first letter t (upper or lower) with X 'This is sparta!'.replace(/t/i, 'X'); //result: 'Xhis is sparta!' //Replace all the Ts in the text (upper or lower) with X 'This is sparta!'.replace(/t/gi, 'X' ); //result: 'Xhis is sparXa!'
```

For more information see the [JavaScript RegExp Object Reference](http://www.w3schools.com/jsref/jsref_obj_regexp.asp "W3C JavaScript RegExp Object Reference") at the w3schools.

# three dots

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

**Spread syntax** allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.

[https://stackoverflow.com/questions/31048953/what-do-these-three-dots-in-react-do](https://stackoverflow.com/questions/31048953/what-do-these-three-dots-in-react-do)

This is a feature of es6 which is used in React as well. Look at the below example:

```
function Sum(x,y,z) { return x + y + z; } console.log(Sum(1,2,3)); //6
```

This way is fine if we have maximum 3 parameters but what if we need to add for example 110 parameters. Should we define them all and add them one by one?! Of course there is an easier way to do which is called SPREAD. Instead of passing all those parameters you write :

```
function (...numbers){}
```

We have no idea how many parameters we have but we know there are heaps of those. Based on es6 we can rewrite the above function as below and use the spread and mapping between them to make it as easy as a piece of cake:

```
let Sum = (...numbers) => { return numbers.reduce((prev, current) => prev + current ); } console.log(Sum(1, 2, 3, 4, 5, 6, 7, 8, 9));//45
```

# get ascii code from  character

[https://stackoverflow.com/questions/94037/convert-character-to-ascii-code-in-javascript](https://stackoverflow.com/questions/94037/convert-character-to-ascii-code-in-javascript)

[`String.prototype.charCodeAt()`](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String/charCodeAt) can convert string characters to ASCII numbers. For example:

```
"ABC".charCodeAt(0) // returns 65
```

For opposite use [`String.fromCharCode(10)`](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String/fromCharCode) that convert numbers to equal ASCII character. This function can accept multiple numbers and join all the characters then return the string. Example:

```
String.fromCharCode(65,66,67); // returns 'ABC'
```

# function like range in C#

[https://www.codewars.com/kata/reversed-sequence/train/javascript](https://www.codewars.com/kata/reversed-sequence/train/javascript)

[https://stackoverflow.com/questions/3895478/does-javascript-have-a-method-like-range-to-generate-a-range-within-the-supp](https://stackoverflow.com/questions/3895478/does-javascript-have-a-method-like-range-to-generate-a-range-within-the-supp)

[https://stackoverflow.com/questions/19544452/remove-last-item-from-array](https://stackoverflow.com/questions/19544452/remove-last-item-from-array)

const reverseSeq = n => {
var temp = [...Array(n + 1).keys()].reverse();
temp.pop();
return temp;
};

Use the [`Array.filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) method:

```
myArray = myArray.filter( function( el ) { return toRemove.indexOf( el ) < 0; } );
```

* * *

Small improvement, as browser support for [`Array.includes()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) has increased:

```
myArray = myArray.filter( function( el ) { return !toRemove.includes( el ); } );
```

* * *

Next adaption using [arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions):

```
myArray = myArray.filter( ( el ) => !toRemove.includes( el ) );
```

# 对char表示的数字做加减运算的时候

直接在变量前面放1个+号，就可以

[https://www.codewars.com/kata/57eaeb9578748ff92a000009/solutions/javascript](https://www.codewars.com/kata/57eaeb9578748ff92a000009/solutions/javascript)

Given an array of integers as strings and numbers, return the sum of the array values as if all were numbers.

Return your answer as a number.

```
function sumMix(x){ return x.map(a => +a).reduce((a, b) => a + b); }
```

[https://stackoverflow.com/questions/15129137/what-does-mean-in-javascript](https://stackoverflow.com/questions/15129137/what-does-mean-in-javascript) 

```
r = +_; 
```

*   `+` tries to cast whatever `_` is to a number.
*   `_` is only a variable name (not an operator), it could be `a`, `foo` etc.

**Example:**

```
+"1" 
```

cast "1" to pure number 1.

```
var _ = "1";
var r = +_; 
```

`r` is now `1`, not `"1"`.

Moreover, according to the [MDN page on Arithmetic Operators](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Operators/Arithmetic_Operators#-_.28Unary_Negation.29):

> The unary plus operator precedes its operand and evaluates to its operand but **attempts to converts it into a number, if it isn't already**. *[...]* It can convert string representations of integers and floats, as well as the non-string values `true`, `false`, and `null`. Integers in both decimal and hexadecimal (`"0x"`-prefixed) formats are supported. Negative numbers are supported (though not for hex). If it cannot parse a particular value, it will evaluate to `NaN`.

It is also noted that

> unary一元 plus is the fastest and preferred way of converting something into a number

```
var sentence = 'The quick brown fox jumps over the lazy dog.'; var word = 'fox';

console.log(`The word "${word}" ${sentence.includes(word)? 'is' : 'is not'} in the sentence`); // expected output: "The word "fox" is in the sentence"
```

# 函数内部检查，被调用的时候，外部是否进行了传参

[https://stackoverflow.com/questions/411352/how-best-to-determine-if-an-argument-is-not-sent-to-the-javascript-function](https://stackoverflow.com/questions/411352/how-best-to-determine-if-an-argument-is-not-sent-to-the-javascript-function)

 `null` is a specific value. `undefined` is what it will be if it is not passed.

# 让一个单词的首字母大写

[https://stackoverflow.com/questions/1026069/how-do-i-make-the-first-letter-of-a-string-uppercase-in-javascript](https://stackoverflow.com/questions/1026069/how-do-i-make-the-first-letter-of-a-string-uppercase-in-javascript)

```
function capitalizeFirstLetter(string) { return string.charAt(0).toUpperCase() + string.slice(1);
}
```

# usage of Date

[https://stackoverflow.com/questions/2698725/comparing-date-part-only-without-comparing-time-in-javascript](https://stackoverflow.com/questions/2698725/comparing-date-part-only-without-comparing-time-in-javascript)

[https://www.codewars.com/kata/is-the-date-today/train/javascript](https://www.codewars.com/kata/is-the-date-today/train/javascript)

```
function isToday(date) { var today = new Date(); var date1 = new Date(Date.UTC(date.getFullYear(), date.getMonth(), date.getDate())); var date2 = new Date(Date.UTC(today.getFullYear(), today.getMonth(), today.getDate())); return date1.getTime() === date2.getTime();
}
```

 其他人更简单的解法

```
function isToday(date) { return new Date().toDateString() === date.toDateString();
}
```

# 判断参数是否为数字

[https://stackoverflow.com/questions/6449611/check-whether-a-value-is-a-number-in-javascript-or-jquery](https://stackoverflow.com/questions/6449611/check-whether-a-value-is-a-number-in-javascript-or-jquery)

```
function isNumber(n) { return !isNaN(parseFloat(n)) && isFinite(n);
}
```

# 没有做完的

//https://www.codewars.com/kata/closest-elevator/train/javascript
function elevator(left, right, call) {
console.log(`${left},${right},${call}`);
var middle = (left + right) / 2;
var delta1 = 0;
var delta2 = 0;
if (left <= right) {
delta1 = Math.abs(middle - left);
delta2 = Math.abs(right - middle);
} else {
delta1 = Math.abs(middle - right);
delta2 = Math.abs(left - middle);
}
var result = 'left';
if (left === right) {
result = 'right';
} else {
if (call <= left) {
result = 'left';
} else if (call >= right) {
result = 'right';
} else {
if (delta2 >= delta1) {
result = 'right';
}
}
}
return result;
}