<!--yml
category: codewars
date: 2022-08-13 11:45:53
-->

# [CodeWars][JS]实现链式加法_weixin_33950035的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_33950035/article/details/93543375?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-93543375.nonecase](https://blog.csdn.net/weixin_33950035/article/details/93543375?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-93543375.nonecase)

在知乎上看到这样一个问题：http://www.zhihu.com/question/31805304;

简单地说就是实现这样一个add函数:

add(x1)(x2)(x3)...(xn) == x1 + x2 + x3 + ... + xn // true;

正好发现在codewars上也有这道题，那不妨一块刷了吧。

# **Kata Description**

**level：5 kyu**

*We want to create a function that will add numbers together when called in succession.*

 *We also want to be able to continue to add numbers to our chain.*

```
add(1)(2)(3); // 6
add(1)(2)(3)(4); // 10
add(1)(2)(3)(4)(5); // 15 
```

* and so on...*

*Test cases:*

```
Test.expect(add(1) == 1);
Test.expect(add(1)(2) == 3);
Test.expect(add(1)(2)(3) == 6); 
```

# **Solution**

首先，第一个示例似乎表示add(1)(2)应该返回数字3，但如此一来add(1)(2)(3)岂不是将函数调用应用在了一个数字上面？

我们再来看这道题提供的Test Cases， 注意cases里使用的是'=='而不是'==='，也就是说返回值不需要是一个数字，只需要是一个能进行类型转换以变成数字的‘值’就可以了。而这道题中，因为add可以连续调用，所以这个‘值’应该是一个函数。

 那么我们要解决的第一个问题： 怎样能使得函数转化为数字？

## **问题一 怎样将函数与数字联系起来**

### 1.valueOf() 方法。

顾名思义，这个方法返回的是调用这个对象的‘值’。

默认情况下一个函数调用valueOf()方法，返回值是函数本身

```
var fn = function(num){return ++num;};
fn(1); // 2
(fn.valueOf())(1); // 2
```

然而这并没有什么卵用。

在这个题目里，我们需要重写这个方法：

```
var fn = function () {}; 
fn.valueOf = function(){ return 233;}; 
console.log(fn==233); // true 
console.log(fn===233); //false 
```

 以上我们可以发现，当 == 对函数对象进行类型转化的时候，会读取函数的valueOf的返回值，这样就达到了我们的目的。

实际上Function本身并没有valueOf方法，该方法继承自Object.prototype.valueOf();

也就是说，不仅仅是函数，当我们需要对任何对象与数字进行比较的时候，都能够使用这个方法。

```
var o = {};
o.valueOf = function(){return 233;};
console.log(o == 233) // true
console.log(o === 233) // false
```

另外，与Function不同，Number，String这些对象，都有着自己的valueOf方法，而非继承于Object。

所以我们可以猜测，==符进行类型转化的时候，可能都是先读取对象的valueOf的返回值进行比较。

### 2\. toString()方法。

除了用上面的valueOf方法以外，toString也可以达到同样的目的。

```
var fn = new Function;
fn.toString = function() { return 233;};
console.log(fn==233); // true
console.log(fn===233); //false
```

和valueOf不同的是，Function中的toString并非继承自Object，它使用的是自己的toString方法。

对于函数而言，toString的返回值就像是调用函数的‘名字’。修改了toString， 就好像给函数换了个‘称号’：

```
var fn = function(){};
console.log(fn); // function()

var fn2 = function(){};
fn2.toString = function(){return 233;};
console.log(fn2) // 233
```

默认调用toString返回的值是该函数的字符串形式，就像对这段代码进行了反编译。

```
var fn = function(){ //Can you see me?
   //Oh..
  return 233;
}; var fnStr = fn.toString();
console.log(fnStr);
```

输出

```
'function (){
  //Can you see me?
   //Oh..
  return 233;
}' 
```

 嗯没错连函数里的注释，换行，空格什么的都包括进来了。

另外MDN的文档说toString()还可以接受一个缩进的参数，不过我试了试好像没有什么用。

### 3\. toString() 与 valueOf()

既然上面两种方法都可以，那么在这个题目里，如果同时使用了这两种方法，那种的优先级更高呢？

这个简单，我们来试一试：

```
var fn = function(){};
fn.toString = function(){return 'toString wins';};
fn.valueOf = function() {return 'valueOf wins';}
fn == 'toString wins'; // false
fn == 'valueOf wins'; // true
```

看来是valueOf()等级更高啊。

也就是说，使用==符对对象与普通数据进行比较的时候，先读取对象的‘value’，如果value不是普通数据类型，再读取‘string’，如果还不是，那就输出false。当然，在读取过程中，如果读取到了普通数据类型并且判断为不等，那就直接输出fasle，不会进行下一步的比较。

**问题二 然后呢**

上面的问题解决后这个题也就解决得差不多了。

首先我们的add函数应该返回一个函数，并且我们需要对这个函数的valueOf（或者toString）进行重写：

```
var add=function(num){
　var inner = function(){};
  inner.valueOf=function(){}; return inner;
};
```

然后用一个temp变量来存储累加的结果吧，temp同时也应该是内部函数的valueOf的返回值：

```
var add=function(num){ var temp = num; var inner = function(num2){};
  inner.valueOf=function(){
 return temp;
  }; return inner;
};
```

 最后补全内部函数的主体部分，因为这个函数要能够不停地被调用，所以inner函数的返回值应该是它本身：

```
var add=function(num){ var temp = num; var inner = function(num2){
    temp+=num2; return inner;
  };
  inner.valueOf=function(){
 return temp;
  }; return inner;
};
```

到此大功告成，submit， pass！

到这里这道题告一段落，不过呢我发现上面的解决方案里完美的解决方案还有一定距离，在我提交代码并看了排名靠前的代码后……

比如temp这个变量是必须的吗？

代码里出现了两次 return inner；是不是有些冗余的感觉呢？

……