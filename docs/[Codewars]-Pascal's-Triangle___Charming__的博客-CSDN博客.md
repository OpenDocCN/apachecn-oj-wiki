<!--yml
category: codewars
date: 2022-08-13 11:45:51
-->

# [Codewars]-Pascal's Triangle___Charming__的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41882147/article/details/79672670?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-79672670.nonecase](https://blog.csdn.net/qq_41882147/article/details/79672670?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-79672670.nonecase)

### [Codewars]-Pascal’s Triangle

#### 题目：

*   就是杨辉三角
*   让你输出三角形的全部元素，以数组的方式

#### 思路：

*   既然杨辉三角的下一列，除了左右两元素是1之外，中间元素是根据上一列得来的。
*   我们模仿这个思路就行了

#### 解答：

```
function pascalsTriangle(n) {

  var cur = [1,1]
  var result = [1,1,1]

  if(n==1){return [1]}
  if(n==2){return result}

  for(var i = 2 ; i < n ; i ++){
    var next = [1]      
    for(var j = 0 ; j < cur.length-1  ; j ++){
        next.push(cur[j]+cur[j+1])
    }
    next.push(1)
    cur = next;
    result = result.concat(next)
  }
  return result
}
```

#### codewar的优秀答案：

*   递归方法，研究下元素和下标的关系可做出来
*   from：`tjwudi, matrixorz, Ulisses`

```
function pascalsTriangle(n) {
  if (n === 1) {
    return [1];
  }
  var prev = pascalsTriangle(n - 1), len = prev.length;
  prev.push(1);
  for (var i = len - n + 1; i < len - 1; i ++) {
    prev.push(prev[i] + prev[i + 1]);
  }
  prev.push(1);
  return prev;
}
```