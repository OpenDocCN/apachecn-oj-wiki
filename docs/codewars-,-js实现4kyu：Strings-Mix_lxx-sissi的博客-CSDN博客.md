<!--yml
category: codewars
date: 2022-08-13 11:42:07
-->

# codewars , js实现4kyu:Strings Mix_lxx-sissi的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_35438535/article/details/106159950?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-4-106159950-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/sinat_35438535/article/details/106159950?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-4-106159950-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# 题目描述

**该kata的链接地址: [link](https://www.codewars.com/kata/5629db57620258aa9d000014).**

Given two strings s1 and s2, we want to visualize how different the two strings are. We will only take into account the lowercase letters (a to z). First let us count the frequency of each lowercase letters in s1 and s2.

s1 = “A aaaa bb c”

s2 = “& aaa bbb c d”

s1 has 4 ‘a’, 2 ‘b’, 1 ‘c’

s2 has 3 ‘a’, 3 ‘b’, 1 ‘c’, 1 ‘d’

So the maximum for ‘a’ in s1 and s2 is 4 from s1; the maximum for ‘b’ is 3 from s2\. In the following we will not consider letters when the maximum of their occurrences is less than or equal to 1.

We can resume the differences between s1 and s2 in the following string: “1:aaaa/2:bbb” where 1 in 1:aaaa stands for string s1 and aaaa because the maximum for a is 4\. In the same manner 2:bbb stands for string s2 and bbb because the maximum for b is 3.

The task is to produce a string in which each lowercase letters of s1 or s2 appears as many times as its maximum if this maximum is strictly greater than 1; these letters will be prefixed by the number of the string where they appear with their maximum value and :. If the maximum is in s1 as well as in s2 the prefix is =:.

In the result, substrings (a substring is for example 2:nnnnn or 1:hhh; it contains the prefix) will be in decreasing order of their length and when they have the same length sorted in ascending lexicographic order (letters and digits - more precisely sorted by codepoint); the different groups will be separated by ‘/’. See examples and “Example Tests”.

Hopefully other examples can make this clearer.

s1 = “my&friend&Paul has heavy hats! &”
s2 = “my friend John has many many friends &”
mix(s1, s2) --> “2:nnnnn/1:aaaa/1:hhh/2:mmm/2:yyy/2:dd/2:ff/2:ii/2:rr/=:ee/=:ss”

s1 = “mmmmm m nnnnn y&friend&Paul has heavy hats! &”
s2 = “my frie n d Joh n has ma n y ma n y frie n ds n&”
mix(s1, s2) --> “1:mmmmmm/=:nnnnnn/1:aaaa/1:hhh/2:yyy/2:dd/2:ff/2:ii/2:rr/=:ee/=:ss”

s1=“Are the kids at home? aaaaa fffff”
s2=“Yes they are here! aaaaa fffff”
mix(s1, s2) --> “=:aaaaaa/2:eeeee/=:fffff/1:tt/2:rr/=:hh”
Note for Swift, R, PowerShell
The prefix =: is replaced by E:

s1 = “mmmmm m nnnnn y&friend&Paul has heavy hats! &”
s2 = “my frie n d Joh n has ma n y ma n y frie n ds n&”
mix(s1, s2) --> “1:mmmmmm/E:nnnnnn/1:aaaa/1:hhh/2:yyy/2:dd/2:ff/2:ii/2:rr/E:ee/E:ss”

# 测试案例

```
Test.describe("Mix",function() {
Test.it("Basic tests",function() {    
    Test.assertEquals(mix("Are they here", "yes, they are here"), "2:eeeee/2:yy/=:hh/=:rr")
    Test.assertEquals(mix("looping is fun but dangerous", "less dangerous than coding"), "1:ooo/1:uuu/2:sss/=:nnn/1:ii/2:aa/2:dd/2:ee/=:gg")
    Test.assertEquals(mix(" In many languages", " there's a pair of functions"), "1:aaa/1:nnn/1:gg/2:ee/2:ff/2:ii/2:oo/2:rr/2:ss/2:tt")
    Test.assertEquals(mix("Lords of the Fallen", "gamekult"), "1:ee/1:ll/1:oo")
    Test.assertEquals(mix("codewars", "codewars"), "")
    Test.assertEquals(mix("A generation must confront the looming ", "codewarrs"), "1:nnnnn/1:ooooo/1:tttt/1:eee/1:gg/1:ii/1:mm/=:rr")
})}) 
```

# 代码实现

## 我完成的代码

```
function mix(s1,s2){

              let result = [],objS1 = cal(s1),objS2 = cal(s2)

              for(let i in objS1){

                if(objS2[i]){
                  objS1[i] > objS2[i] && result.push('1:'+i.repeat(objS1[i]))   
                  objS1[i] < objS2[i] && result.push('2:'+i.repeat(objS2[i]))
                  objS1[i] == objS2[i] && result.push('=:'+i.repeat(objS1[i])) 
                }else{
                  result.push('1:'+i.repeat(objS1[i])) 
                }
              } 

              for(let i in objS2){
                   !objS1[i] && result.push('2:'+i.repeat(objS2[i]))
              }        

              function cal(str){
                  var obj = {};

                  str.replace(/[^a-z]/g,'').split('').map(x => obj[x] ? obj[x] ++ : obj[x] = 1)

                  for(let i in obj){
                    obj[i] == 1 &&　delete obj[i]
                  }

                  return obj
              }

      return result.sort(function(a,b){return (b.length - a.length) || (a < b ? -1 : 1);}).join('/')
 } 
```

## 解题步骤(表达能力不是太好…)

1.对传入的字符串进行处理：计算出各个小写字母出现的次数，并删除只出现了一次字母

2.对两个处理之后的结果objS1、objS2进行比较：循环objS1（或者objS2）的属性，

如果objS2里也存在该属性，则：
如果该属性在objS2里存在的数量多于objS1，就按题目以objS2的名义将该属性（并对应在objS2中的数量）存入result中；
如果该属性在objS1里存在的数量多于objS2，就按题目以objS1的名义将该属性（并对应在objS1中的数量）存入result中；
如果相等，就按题目以"相等"的名义将该属性（并对应数量）存入result中;

如果objS2里不存在该属性，就按题目以objS1的名义将该属性（并对应在objS1中的数量）存入result中。

然后循环objS2的属性，将在objS1里不存在的属性按题目以objS2的名义将该属性（并对应在objS2中的数量）存入result中。

3.对得出的数组result按长度和字母顺序排序并转化为字符串

## 难点

这个题的难点对于我来说就是得出结果之后的排序，由于对.sort()的运用不是很熟悉，所以在这部分浪费了很多时间，最后还是百度了一下用法，虽然得出了最后的结果，但还是对这部分一知半解，果然还是只会切图的小菜鸟。。。。。。