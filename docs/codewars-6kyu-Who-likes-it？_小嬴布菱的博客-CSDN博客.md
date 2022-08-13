<!--yml
category: codewars
date: 2022-08-13 11:44:32
-->

# codewars 6kyu Who likes it?_小嬴布菱的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_29549685/article/details/117340472?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-117340472.nonecase](https://blog.csdn.net/qq_29549685/article/details/117340472?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-117340472.nonecase)

codewars [6kyu Who likes it?](https://www.codewars.com/kata/5266876b8f4bf2da9b000362/train/javascript)

这个题没啥难度，就是根据题意输出字符串。

```
function likes(names) {

  ans = '';
  if(names.length == 0){
    ans += 'no one likes this';
  }  else if(names.length == 1){
    ans += names[0] + ' likes this';
  }else if(names.length == 2){
    ans += names[0]+' and '+names[1] + ' like this';
  }else if(names.length == 3){
    ans += names[0]+', '+names[1]+' and '+names[2] + ' like this';
  }else{
    ans += names[0]+', '+names[1]+' and '+(names.length-2)+' others' + ' like this';
  }
  return ans;
} 
```

用python用习惯了都忘记了可以使用switch，case

```
function likes(names) {
  names = names || [];
  switch(names.length){
    case 0: return 'no one likes this'; break;
    case 1: return names[0] + ' likes this'; break;
    case 2: return names[0] + ' and ' + names[1] + ' like this'; break;
    case 3: return names[0] + ', ' + names[1] + ' and ' + names[2] + ' like this'; break;
    default: return names[0] + ', ' + names[1] + ' and ' + (names.length - 2) + ' others like this';
  }
} 
```

还有其他新奇的解法

```
function likes(names) {
  return {
    0: 'no one likes this',
    1: `${names[0]} likes this`, 
    2: `${names[0]} and ${names[1]} like this`, 
    3: `${names[0]}, ${names[1]} and ${names[2]} like this`, 
    4: `${names[0]}, ${names[1]} and ${names.length - 2} others like this`, 
  }[Math.min(4, names.length)]
} 
```

```
function likes (names) {
  var templates = [
    'no one likes this',
    '{name} likes this',
    '{name} and {name} like this',
    '{name}, {name} and {name} like this',
    '{name}, {name} and {n} others like this'
  ];
  var idx = Math.min(names.length, 4);

  return templates[idx].replace(/{name}|{n}/g, function (val) {
    return val === '{name}' ? names.shift() : names.length;
  });
} 
```