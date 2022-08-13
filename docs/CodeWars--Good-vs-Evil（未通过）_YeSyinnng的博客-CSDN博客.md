<!--yml
category: codewars
date: 2022-08-13 11:48:41
-->

# CodeWars -Good vs Evil（未通过）_YeSyinnng的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_39532595/article/details/86540922?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-86540922.nonecase](https://blog.csdn.net/qq_39532595/article/details/86540922?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-86540922.nonecase)

这是一个没有通过的并且找不到错误的一个题目，我自己找不到啊，先放上来，看看有没有大佬能够给我看看。。。

题目：

> ```
> will have many battles with the forces of evil. Different races will
> certainly be involved. Each race has a certain worth when battling
> against others. On the side of good we have the following races, with
> their associated worth:
> 
> Hobbits: 1 Men: 2 Elves: 3 Dwarves: 3 Eagles: 4 Wizards: 10 On the
> side of evil we have:
> 
> Orcs: 1 Men: 2 Wargs: 2 Goblins: 2 Uruk Hai: 3 Trolls: 5 Wizards: 10
> Although weather, location, supplies and valor play a part in any
> battle, if you add up the worth of the side of good and compare it
> with the worth of the side of evil, the side with the larger worth
> will tend to win.
> 
> Thus, given the count of each of the races on the side of good,
> followed by the count of each of the races on the side of evil,
> determine which side wins.
> 
> Input: The function will be given two parameters. Each parameter will
> be a string separated by a single space. Each string will contain the
> count of each race on the side of good and evil.
> 
> The first parameter will contain the count of each race on the side of
> good in the following order:
> 
> Hobbits, Men, Elves, Dwarves, Eagles, Wizards. The second parameter
> will contain the count of each race on the side of evil in the
> following order:
> 
> Orcs, Men, Wargs, Goblins, Uruk Hai, Trolls, Wizards. All values are
> non-negative integers. The resulting sum of the worth for each side
> will not exceed the limit of a 32-bit integer.
> 
> Output: Return "Battle Result: Good triumphs over Evil" if good wins,
> "Battle Result: Evil eradicates all trace of Good" if evil wins, or
> "Battle Result: No victor on this battle field" if it ends in a tie. 
> ```

我的见解： 就是给两字符串，然后里面的内容都是数字，并且是用空格相隔开的数据，先分隔成数组，然后根据获取数据相加，但是有错误啊，codewar有一点不好就是，我看不见测试数据啊！！

代码：

```
function goodVsEvil(good, evil){
    let goodRes = change(good);
    let evilRes = change(evil);
    let str;
    if(goodRes===evilRes){
       str= "Battle Result: No victor on this battle field";
    }else{
        goodRes >evilRes? str= 'Battle Result: Good triumphs over Evil':str="Battle Result: Evil eradicates all trace of Good";
    }
    return str;
 }

 function change(name){
     var str1 = name.split(' ');   
     var num =0;
     for(var i=0;i<str1.length;i++){
         num+=parseInt(str1[i]);
     }
     return num;
 } 
```

显示通过93个 没有通过28个 ，好密码。。

给予的三个测试例子：

```
Test.expect( goodVsEvil('1 1 1 1 1 1', '1 1 1 1 1 1 1') === 'Battle Result: Evil eradicates all trace of Good', 'Evil should win' );
Test.expect( goodVsEvil('0 0 0 0 0 10', '0 1 1 1 1 0 0') === 'Battle Result: Good triumphs over Evil', 'Good should win' );
Test.expect( goodVsEvil('1 0 0 0 0 0', '1 0 0 0 0 0 0') === 'Battle Result: No victor on this battle field', 'Should be a tie' );
`
唉~！`` 
```