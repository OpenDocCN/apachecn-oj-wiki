<!--yml
category: codewars
date: 2022-08-13 11:43:08
-->

# CodeWars - Who likes it?_YeSyinnng的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_39532595/article/details/86516845?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-86516845.nonecase](https://blog.csdn.net/qq_39532595/article/details/86516845?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-86516845.nonecase)

来~

题目：

> /**You probably know the “like” system from Facebook and other pages.
> People can “like” blog posts, pictures or other items.
> We want to create the text that should be displayed next to such an item.
> Implement a function likes :: [String] -> String, which must take in input array,
> containing the names of people who like an item.
> It must return the display text as shown in the examples:
> likes [] // must be “no one likes this”
> 空数组的时候 输出no one + likes this
> likes [“Peter”] // must be “Peter likes this”
> 一个数据的时候就 人名 + likes this
> likes [“Jacob”, “Alex”] // must be “Jacob and Alex like this”
> 两个数据的时候 one and two like this
> likes [“Max”, “John”, “Mark”] // must be “Max, John and Mark like this”
> 三个数据的时候 one,two and three like this
> likes [“Alex”, “Jaco”, “Mark”, “Max”] // must be “Alex, Jacob and 2 others like this”
> 四个数据 one,two and
> names 是一个数组
> */

代码

```
function likes(names) {
  // TODO
  while(names.length){
    if(names.length==1){
        return names[0]+' likes this';
    }else if(names.length==2){
        return names[0]+' and '+names[1] +' like this';
    }else if(names.length==3){
        return names[0]+', '+names[1]+" and " +names[2]+" like this";
    }else {
        return names[0]+', '+names[1]+" and "+(names.length-2)+" others like this";
    }
  }
  return "no one likes this";
} 
```

也可以用switch 进行

```
function likes(names) {
  names = names || [];    //没有内容的时候 就给长度为0
  switch(names.length){
    case 0: return 'no one likes this'; break;
    case 1: return names[0] + ' likes this'; break;
    case 2: return names[0] + ' and ' + names[1] + ' like this'; break;
    case 3: return names[0] + ', ' + names[1] + ' and ' + names[2] + ' like this'; break;
    default: return names[0] + ', ' + names[1] + ' and ' + (names.length - 2) + ' others like this';
  }
} 
```

大神的，打扰了~！正则，正则！！ 正则不是一天练成的，是很多天！！！

```
 function likes (names) {
  var templates = [
    'no one likes this',
    '{name} likes this',
    '{name} and {name} like this',
    '{name}, {name} and {name} like this',
    '{name}, {name} and {n} others like this'
  ];
  var idx = Math.min(names.length, 4);  //取最小值

  return templates[idx].replace(/{name}|{n}/g, function (val) {
    return val === '{name}' ? names.shift() : names.length;
  });
} 
```