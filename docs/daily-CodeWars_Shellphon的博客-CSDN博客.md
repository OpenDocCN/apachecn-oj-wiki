<!--yml
category: codewars
date: 2022-08-13 11:49:07
-->

# daily CodeWars_Shellphon的博客-CSDN博客

> 来源：[https://blog.csdn.net/dont27/article/details/38695413?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-38695413.nonecase](https://blog.csdn.net/dont27/article/details/38695413?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-38695413.nonecase)

*   Javascript filter - 1

    ```
    function searchNames(logins){
      return logins.filter(function(login){return /_$/.test(login[0])});
    } 
    ```

*   The range() function

    ```
    function range(start, end, step) {
    step = step===undefined?1:step;
    if(end===undefined){
     end = start;
     start = 0;
    }
    if(end==0){
     return [];
    }
    var res = [start];
    if(step!=0){
     while(start+step<end){
       start += step;
       res.push(start);
     }
    }else{
     for(var i=2; i<end;i++){
       res.push(start);
     }
    }
    return res;
    } 
    ```

*   Convert a Number to a String!

    ```
    function numberToString(num){
      return ''+num;
    } 
    ```

*   Who likes it?

    ```
    function likes(names) {
    var res='',
        len = names.length;
    switch(len){
      case 0:
        res = 'no one likes this';
        break;
      case 1:
        res = names[0] + " likes this";
        break;
      case 2:
        res = names[0]+" and "+ names[1]+ " like this";
        break;
      case 3:
        res = names[0]+", "+ names[1]+" and "+names[2] + " like this";
        break;
      default:
        res = names[0]+", "+ names[1]+" and "+(names.length-2) +" others like this";
        break;
    }
    return res;
    } 
    ```

*   Naughty or Nice?

    ```
    function getNiceNames(people){
    return people.filter(function(per){
      return per.wasNice;
    }).map(function(e){return e.name});
    }
    function getNaughtyNames(people){
    return people.filter(function(per){
      return !per.wasNice;
    }).map(function(e){return e.name});
    } 
    ```

*   return a sorted list of objects

    ```
    function sortList (sortBy, list) {
    return list.sort(function(a, b){return parseInt(b[sortBy])-parseInt(a[sortBy])});
    } 
    ```

*   Find the Remainder

    ```
    function remainder(a, b){
    return Math.max(a,b)%Math.min(a,b);
    } 
    ```

*   Building Strings From a Hash

    ```
    function solution(pairs){
                        var re="";
                        for(var i in pairs){
                          re += i+" = "+pairs[i]+','
                        }
                        return re.substring(0,re.length-1);
    } 
    ```

*   Array.diff

    ```
     function array_diff(a, b) {
    return a.filter(function(e){return b.indexOf(e)==-1});
    } 
    ```

*   No oddities here

    ```
    function noOdds( values ){
    return values.filter(function(e){return e%2==0;});
    } 
    ```

*   Flatten

    ```
     var flatten = function (array){
    var res = [],
       len = array.length;
    for(var i=0;i<len;i++){
     var ar = array[i];
     if(ar instanceof Array){
       for(var j=0;j<ar.length;j++){
         res.push(ar[j]);
       }
     }else{
         res.push(ar);
     }
    }
    return res;
    }

    var flatten = function (array){
    return [].concat.apply([],array);
    } 
    ```

*   Mr.Freeze

    ```
     Object.freeze(MrFreeze); 
    ```

*   Pluck

    ```
    function pluck(objs, name) {
    return objs.map(function(obj){
      return obj[name];
    });
    } 
    ```

*   Reverse words

    ```
     function reverseWords(str) {
      return str.split(" ").map(function(a){
       return a.split('').reverse().join('');
     }).join(" ");
    } 
    ```

*   Get key/value pairs as arrays

    ```
    function keysAndValues(data){
    var keys=[],
        values=[],
        res = [];
    for(var key in data){
      keys.push(key);
      values.push(data[key]);
    }
    res.push(keys);
    res.push(values);
    return res;
    }

    function keysAndValues(data){
      return [Object.keys(data)].push(Object.keys(data).map(function(e){return data[e]}));
    } 
    ```

*   SantaClausable Interface

    ```
     function isSantaClausable(obj) {
     return (typeof obj.sayHoHoHo =='function')
     &&(typeof obj.distributeGifts == 'function')
     &&(typeof obj.goDownTheChimney == 'function');
    }

    function isSantaClausable(obj) {
      return ['sayHoHoHo','distributeGifts','goDownTheChimney'].every(function(m){return typeof obj[m]=='function'});
    } 
    ```

*   Disemvowel Trolls

    ```
    function disemvowel(str) {
    return str.split('').map(function(e){
      if(['e','i','o','a','u','A','O','E','I','U'].indexOf(e)==-1){
        return e;
      }
    }).join('');
    }

    function disemvowel(str) {
    return str.replace(/[aeiou]/gi, '');
    } 
    ```

*   Summing a number's digits

    ```
    function sumDigits(number) {
      var sum = 0;
    (number<0?(-number)+'':number+'').split('').forEach(function(e){sum+=parseInt(e)});
    return sum;
    } 
    ```

*   Number Of Occurrences

    ```
    Array.prototype.numberOfOccurrences = function() {
    if(arguments.length<1){
      return 0;
    }
    var times = 0,
        arg = arguments[0];
    this.forEach(function(e){
      if(e===arg){
        times++;
      }
    });
    return times;
    }

    Array.prototype.numberOfOccurrences = function(search){
      return this.filter(function(num){return search===num}).length;
    }; 
    ```

*   Count characters in your string

    ```
    function count (string) {  
     var res = {};
     var str = string.split('').forEach(function(e){
       res[e] = res[e]?res[e]+1:1;
     });
     return res;
    } 
    ```

*   Reversed Strings

    ```
    function solution(str){
    return str.split('').reverse().join('');
    } 
    ```

*   Sentence Smash

    ```
    function smash (words) {
     "use strict";
      return words.join(' ');
    }; 
    ```

*   Sort the Gift Code

    ```
    function sortGiftCode(code){
    return code.split('').sort().join(''); 
    } 
    ```

*   Remove anchor from URL

    ```
    function removeUrlAnchor(url){
    return url.split('#')[0];
    } 
    ```

*   Basic Training: Add item to an Array

    ```
    websites.push('codewars'); 
    ```

*   Anything to integer

    ```
    function toInteger(n) {
    var num = Number(n)+'';
    var t= num.split('\.')[0];
    if(num=='Infinity'||num=='NaN')return 0;
    return Number(t);
    } 
    ```

*   Is Integer Array ?

    ```
    function isIntArray(arr) {
    return arr instanceof Array?arr.every(function(e){return e!=null &&typeof e != 'string'&&!isNaN(e)&&(e+'').indexOf('.')==-1}):false;
    } 
    ```

*   Return substring instance count

    ```
    function solution(fullText, searchText){
    return fullText.split(searchText).length-1;
    } 
    ```

*   Sort arrays - 1

    ```
    sortme = function( names ){
    return names.sort();
    } 
    ```

*   Sort arrays - 2

    ```
    sortme = function( names ){
     return names.sort(function(a,b){return a.toLowerCase().localeCompare(b.toLowerCase())})
    } 
    ```

*   Functional Addition

    ```
    function add(n) {
    return function(){
      return arguments[0]+n;
    }
    } 
    ```

*   Function 2 - squaring an argument

    ```
    function square(e){
    return e*e;
    } 
    ```

*   Singleton Pattern

    ```
    var Singleton = function(){
    if(Singleton._instance)return Singleton._instance;
    if(!this instanceof Singleton)return new Singleton();
    Singleton._instance = this;
    }; 
    ```

*   Sentences with Functions

    ```
    function Adam() {return arguments[0]?'Adam '+arguments[0]:'Adam.'}
    function has() {return 'has '+arguments[0]}
    function a() {return 'a '+arguments[0]}
    function dog() {return arguments[0]?'dog '+arguments[0]:'dog.'}
    function The() {return 'The '+arguments[0]}
    function name() {return 'name '+arguments[0]}
    function of() {return 'of '+arguments[0]}
    function the() {return 'the '+arguments[0]}
    function is() {return 'is '+arguments[0]}
    function also() {return 'also '+arguments[0]} 
    ```

*   Elapsed Seconds

    ```
    function elapsedSeconds(startDate, endDate){
    return (Date.parse(endDate)-Date.parse(startDate))/1000;
    } 
    ```

*   Trim a String

    ```
    String.prototype.trim = function() {
    return this.replace(/^\s*/g,'').replace(/\s*$/g,'');
    }; 
    ```

*   Square(n) Sum

    ```
    function squareSum(numbers){
      return numbers.map(function(e){return e*e}).reduce(function(e1,e2){return e1+e2});
    } 
    ```

*   The Coupon Code

    ```
    function checkCoupon(enteredCode, correctCode, currentDate, expirationDate){
    if(enteredCode===correctCode){
      return new Date(currentDate)<=new Date(expirationDate);
    }
    return false;
    } 
    ```

*   Operator overload ?

    ```
    var Foo = function(value) {
    this.val = value;
    }
    Foo.prototype.valueOf = function(){
    return this.val;
    } 
    ```

*   JavaScript class-like objects

    ```
    function Animal(name, type){
    this.name = name;
    this.type = type;
    this.toString = function(){
      return this.name+' is a '+this.type;
    }
    } 
    ```

*   Anagram Detection

    ```
    var isAnagram = function(test, original) {
     var tl = original.toLowerCase();
    return test.length==original.length&&test.toLowerCase().split('').every(function(e){return tl.indexOf(e)>-1})
    }; 
    ```

*   esreveR gnirtS

    ```
    String.prototype.reverse = function(){
    return this.split('').reverse().join('');
    } 
    ```

*   Basic JS - Calculating averages

    ```
    var Calculator = {
    average: function() {
    return arguments.length?Array.prototype.reduce.call(arguments, function(a,b){return a+b})/arguments.length:0;
    }
    }; 
    ```

*   Numerology

    ```
     function solution(date){
    var sum = (date.getDate()+date.getMonth()+1+date.getFullYear());
    return splitsum(splitsum(sum));
    }
    function splitsum(i){
    return Number((''+i).split('').reduce(function(a,b){return parseInt(a)+parseInt(b)}));
    } 
    ```

*   The Vowel Code

    ```
    function encode(string){
    return string.replace(/a/g,1).replace(/e/g,2).replace(/i/g,3).replace(/o/g,4).replace(/u/,5);
    }

    function decode(string){
    return string.replace(/1/g,'a').replace(/2/g,'e').replace(/3/g,'i').replace(/4/g,'o').replace(/5/,'u');
    } 
    ```

*   Number-like counter

    ```
    function Counter(){
    this.val=0;
    this.valueOf =function(){return this.val;}
    }
    Counter.prototype.incr = function() {
    return ++this.val;
    } 
    ```

*   Name Array Capping

    ```
    function capMe(names) {
    return names.map(function(e){
     return e.substr(0,1).toUpperCase()+e.substr(1).toLowerCase();
    });
    } 
    ```

*   Multiplication table

    ```
    multiplicationTable = function(size) {
    var arr = [];
    for(var i=0;i<size;i++){
      arr.push(i+1);
    }
    return arr.map(function(e){
      var r = [];
      for(var j =1;j<size+1;j++){
        r.push(e*j);
      }
      return r;
    });
    } 
    ```

*   Basic JS - Building a calculator

    ```
    var Calculator = {};
    Calculator.add = function(a,b){return a+b}
    Calculator.subtract = function(a,b){return a-b}
    Calculator.multiply = function(a,b){return a*b}
    Calculator.divide = function(a,b){return b?a/b:false} 
    ```

*   Milk and Cookies for Santa

    ```
    function timeForMilkAndCookies(date){
    return date.getMonth()==11&&date.getDate()==24;
    } 
    ```

*   Cylon Evolution

    ```
    function Cylon(model){
    this.model = model;
    this.attack = function(){
      return 'Destroy all humans!';
    };
    }
    function HumanSkin(model){
    this.model = model;
    this.attack = function(){
      return 'Destroy all humans!';
    };
    this.infiltrate = function(){
      return 'Infiltrate the colonies';
    };
    }
    HumanSkin.prototype = new Cylon(); 
    ```

*   Javascript filter - 2

    ```
    function roomMates( rooms, floor ){
    return rooms.filter(function(e,i){return e&&Math.floor(i/6)==floor-1});
    } 
    ```

*   Array Helpers

    ```
    Array.prototype.square = function(){
    return this.map(function(e){return e*e});
    }
    Array.prototype.cube = function(){
    return this.map(function(e){return e*e*e});
    }
    Array.prototype.sum = function(){
    return this.length?this.reduce(function(e,b){return e+b}):0;
    }
    Array.prototype.average = function(){
    return this.sum()/this.length;
    }
    Array.prototype.even = function(){
    return this.filter(function(e){return e%2==0});
    }
    Array.prototype.odd = function(){
    return this.filter(function(e){return e%2});
    } 
    ```

*   Simple elevator

    ```
    function goto(level,button){
    if(typeof level != 'number'|| level<0||level>3||!/[0-3]/.test(button))return 0;
    return parseInt(button)-level;
    } 
    ```

*   Use reduce() to calculate the sum of the values in an array

    ```
    function sum(array) {
    return array.reduce(function(a,b){return a+b});
    } 
    ```

*   Return the Missing Element

    ```
    function getMissingElement(superImportantArray){
    return 45-superImportantArray.reduce(function(a, b){
      return a+b;
    });
    } 
    ```

*   The reject() function

    ```
    function reject(array, iterator) {
    return array.filter(function(e){return !iterator(e)})
    } 
    ```

*   Say "Hello World" JS Style

    ```
    var say = function(string1) {
    return function(string2){
      return string1 + ' '+string2;
    }
    }
    ```