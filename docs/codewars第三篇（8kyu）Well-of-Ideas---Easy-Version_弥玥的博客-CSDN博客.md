<!--yml
category: codewars
date: 2022-08-13 11:47:44
-->

# codewars第三篇（8kyu）Well of Ideas - Easy Version_弥玥的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_37629509/article/details/103614514?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-103614514.nonecase](https://blog.csdn.net/qq_37629509/article/details/103614514?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-103614514.nonecase)

**题目：**
For every good kata idea there seem to be quite a few bad ones!

In this kata you need to check the provided array (x) for good ideas ‘good’ and bad ideas ‘bad’. If there are one or two good ideas, return ‘Publish!’, if there are more than 2 return ‘I smell a series!’. If there are no good ideas, as is often the case, return ‘Fail!’.
**个人认为比较好的解答：**

```
const well = x => {
  const good_count = x.filter(x => x == 'good').length;
  return good_count < 1 ? 'Fail!' : 
         good_count < 3 ? 'Publish!' : 'I smell a series!';
} 
```

```
function well(x) {
  switch (x.filter(i => i === 'good').length) {
    case 0:
      return 'Fail!'
    case 1:
    case 2:
      return 'Publish!'
    default:
      return 'I smell a series!'
  }
} 
```

**自己的解答：**

```
function well(x){
  let num = 0;
  for(let i = 0; i < x.length; i++){
    x[i] === 'good' ? num++ : num;
  }
  if(num > 2){
    return 'I smell a series!';
  } else if(num >= 1 && num <= 2){
    return 'Publish!';
  } else{ 
    return 'Fail!';
  }
} 
```