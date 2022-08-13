<!--yml
category: codewars
date: 2022-08-13 11:36:31
-->

# codewars刷题记录_weixin_34250709的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_34250709/article/details/91435036?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-91435036.142^v40^control,185^v2^control](https://blog.csdn.net/weixin_34250709/article/details/91435036?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-91435036.142^v40^control,185^v2^control)

## 2018-10-19

#### 运算 ： seven(times(five())

```
// 我的
function get(type, i, j) {
  switch (type) {
    case 0:
      return j + i
    case 1:
      return j - i
    case 2:
      return j * i
    case 3:
      return (j - (j % i)) / i
  }
}

function getN(callback, n) {
  if(!callback) return n
  return get(callback[0], callback[1], n)
}

function zero(callback) {
  return getN(callback, 0)
}
function one(callback) {
  return getN(callback, 1)
}
function two(callback) {
  return getN(callback, 2)
}
function three(callback) {
  return getN(callback, 3)
}
function four(callback) {
  return getN(callback, 4)
}
function five(callback) {
  return getN(callback, 5)
}
function six(callback) {
  return getN(callback, 6)
}
function seven(callback) {
  return getN(callback, 7)
}
function eight(callback) {
  return getN(callback, 8)
}
function nine(callback) {
  return getN(callback, 9)
}

function plus(i) { 
  return [0, i]
}
function minus(i) {
  return [1, i]
}
function times(i) {
 return[2, i]
 }
function dividedBy(i) {
 return [3, i]
} 

// 优秀解法
['zero', 'one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine']
.forEach(function (name, n) {
  this[name] = function (f) { return f ? f(n) : n }
});

function plus(n)      { return function (a) { return a + n } }
function minus(n)     { return function (a) { return a - n } }
function times(n)     { return function (a) { return a * n } }
function dividedBy(n) { return function (a) { return a / n } }
复制代码
```

## 2018-10-18

#### 最近两个数之和是否等于第三个数

```
// 我的
function productFib(prod){
  const phi = (1 + Math.sqrt(5))/2
  const fn = (n) => Math.round(Math.pow(phi, n) / Math.sqrt(5))
  for(var i = 1;  fn(i) * fn(i+1) < prod; i++) {}
  return [fn(i), fn(i+1), fn(i)*fn(i+1) === prod]
}

// 优秀解法
function productFib(prod){
  let [a, b] = [0, 1];
  while(a * b < prod) [a, b] = [b, a + b];
  return [a, b, a * b === prod];
}
复制代码
```

#### 求数组中最小2个数之和

> sort(): 如果调用该方法时没有使用参数，将按字母顺序对数组中的元素进行排序，说得更精确点，是按照字符编码的顺序进行排序。要实现这一点，首先应把数组的元素都转换成字符串（如有必要），以便进行比较。
> 
> array.sort()方法默认是升序排序，如果想按照其他标准进行排序，就需要提供比较函数，该函数要比较两个值，然后返回一个用于说明这两个值的相对顺序的数字。比较函数应该具有两个参数 a 和 b，其返回值如下：
> 
> 若 a 小于 b，在排序后的数组中 a 应该出现在 b 之前，则返回一个小于 0 的值。
> 
> 若 a 等于 b，则返回 0。
> 
> 若 a 大于 b，则返回一个大于 0 的值。

```
// 我的
function sumTwoSmallestNumbers(numbers) {  
  //Code here
  const arr = numbers.sort((a, b) => {
  return a-b})
  return (arr[0] + arr[1])
};
// 优秀解法
function sumTwoSmallestNumbers(numbers) {  
  var [ a, b ] = numbers.sort((a, b) => a - b)
  return a + b
}
复制代码
```

#### 编写一个接受10个整数（0到9之间）数组的函数，它以电话号码的形式返回这些数字的字符串

```
createPhoneNumber([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]) // => returns "(123) 456-7890"
复制代码
```

```
// 我的
function createPhoneNumber(numbers){
  const area = numbers.slice(0, 3).join('')
  const num = numbers.slice(3, 6).join('')
  const phone = numbers.slice(6).join('')
  return `(${area}) ${num}-${phone}`
}

// 优秀解法
function createPhoneNumber(numbers){
  var format = "(xxx) xxx-xxxx";

  for(var i = 0; i < numbers.length; i++)
  {
    format = format.replace('x', numbers[i]);
  }

  return format;
}
function createPhoneNumber(numbers){
  return numbers.join('').replace(/(...)(...)(.*)/, '($1) $2-$3');
}
function createPhoneNumber(numbers){
  return numbers.join('').replace(/(\d{3})(\d{3})(\d{4})/,'($1) $2-$3');
}
复制代码
```

## 2018-10-15

#### 从列表a中删除列表b中的所有值

```
// 我的
function array_diff(a, b) {
  const all = [...a, ...b]
  return all.filter(item => a.indexOf(item) > -1 && b.indexOf(item) <= -1)
}

// 优秀解法
function array_diff(a, b) {
  return a.filter(function(x) { return b.indexOf(x) == -1; });
}
function array_diff(a, b) {
  return a.filter(e => !b.includes(e));
}
复制代码
```

#### 求字符串最小单词长度

```
// 我的
function findShort(s){
  let arr = s.split(' ').sort((a, b) => {
    return a.length - b.length
  }) 
  return arr[0].length
}

// 优秀解法
function findShort(s){
  return Math.min.apply(null, s.split(' ').map(w => w.length));
}
复制代码
```

#### 求字符串元音字符个数

```
// 我的
function getCount(str) {
  var vowelsCount = 0;

  // enter your majic here
  const arr = ['a','e','i','o', 'u']
  for(let i = 0; i <= str.length; i++) {
    if(arr.indexOf(str[i]) > -1) {
      vowelsCount ++ 
    }
  }
  return vowelsCount;
}

// 优秀解法
function getCount(str) {
  return (str.match(/[aeiou]/ig)||[]).length;
}
复制代码
```

## 2018-10-11

#### 返回第一个最长的字符串，该字符串由数组中的k个连续字符串组成

```
// 我的
function longestConsec(strarr, k) {
    if(k > strarr.length || k <= 0) {
      return ""
    }    
    let string = ""
    for(var i = 0 ; i <= strarr.length - k ; i ++ ) {
       string = strarr.slice(i, i + k).join('').length > string.length ?  strarr.slice(i, i + k).join('') : string
    }
    return string
}
// 优秀解法
function longestConsec(strarr, k) {
    var longest = "";
    for(var i=0;k>0 && i<=strarr.length-k;i++){
      var tempArray = strarr.slice(i,i+k);
      var tempStr = tempArray.join("");
      if(tempStr.length > longest.length){
        longest = tempStr;
      }
    }
    return longest;
}
复制代码
```