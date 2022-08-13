<!--yml
category: codewars
date: 2022-08-13 11:46:19
-->

# [Codewars]-Find the unknown digit___Charming__的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41882147/article/details/79770138?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-79770138.nonecase](https://blog.csdn.net/qq_41882147/article/details/79770138?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-79770138.nonecase)

### [Codewars]-Find the unknown digit

#### 题目：

*   找到使等式成立的未知数
*   有几条原则：

    *   两个0连续`00`，这是一个不合法的数字
    *   两个减号`--`，其实是一个加号`+`
    *   未知数是等式里未出现过的数字
    *   如果有多个数字使等式成立，返回最小的
    *   如果未找到使等式成立的数字，返回-1

#### 思路

*   看清楚题目的原则时候，直接写代码就行
*   一定要记住的是**未知数是等式里未出现过的数字** ，你就不会有`?*11=??`，为啥返回`2`这个问题了（因为00是不成立的，而且1出现过，故返回2）

#### 解答：

```
function solveExpression(exp) {
  exp = exp.replace('=','==').replace('--','+')
  for(var i = 0 ; i <= 9 ; i ++){
    var flag = exp.indexOf(i)==-1
    var str = exp.replace(/\?/g,i);
    if(/^00/.test(str)||/^00/.test(str.split('==')[1])){continue}
    try{
      if(eval( str )&&flag){
        return i;
        break;
      }
    }catch(e){
    }
  }
  return -1

}
```

```
function solveExpression(exp) {
  exp = exp.replace('=','==').replace('--','+');
  for(var i = 0; i < 10; i++){
    if(eval(exp.replace(/\?/g,i)) && !exp.includes(i)){
        if(!/^00+$/.test(exp.replace(/\?/g,i).split('==')[1]))  return i;
    }
  }
  return -1;
}
```

*   后记：发现大神的做法都是ES6的新东西，自己渣渣还不是很懂es6，要去学一波了。