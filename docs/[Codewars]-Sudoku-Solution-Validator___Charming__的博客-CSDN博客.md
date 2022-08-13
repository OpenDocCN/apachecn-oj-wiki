<!--yml
category: codewars
date: 2022-08-13 11:46:03
-->

# [Codewars]-Sudoku Solution Validator___Charming__的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41882147/article/details/79668106?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-79668106.nonecase](https://blog.csdn.net/qq_41882147/article/details/79668106?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-79668106.nonecase)

### [Codewars]-Sudoku Solution Validator

#### 题目：

*   检查9*9数独矩阵是否有效。
*   根据三个条件判定：

    *   1.每行数字不重复（1~9）
    *   2.每列数字不重复（1~9）
    *   3.9个3*3的九宫格数字不重复（1~9）

#### 思路：

#### 解答：

```
function validSolution(board){

  var len = board.length ; 
  var fanArr = fan(board)

  for(var x = 0 ; x <=6 ; x +=3){
        for(var y = 0 ; y <= 6 ; y += 3){
            var temp = 0
            for(var a = 0 ; a<=2 ; a ++){
                for(var b = 0 ; b <= 2 ; b++){
                    temp +=board[x+a][y+b] 
                }
            }
            if( temp !=45  ){
                return false
                break
            }
        }
     }

    for( let i = 0 ; i < len ; i ++){

        if( isRepeat(board[i])  ){
            return false
        }

        if( isRepeat(fanArr[i])){
            return false
        }
    }
    return true
  function isRepeat(arr){
    arr = arr.sort(function(a,b){return a-b})
    for(var i = arr.length-1 ; i >= 1 ; i --){
        if(arr[i]==arr[i-1]){
            return true
        }
    }
    return false
  }
  function fan(arr){
    var col = arr.length ;
    var cow = arr[0].length;
    var b = [];
    for(var i = 0 ; i < col ; i ++){
        b[i] = []
        for(var j = 0 ; j < cow ; j ++){
            b[i][j] = arr[j][i]
        }
    }
    return b
  }
```

#### 补充下大神的做法

```
function validSolution(board){
  var sumh = [0,0,0,0,0,0,0,0,0];
  var sumv = [0,0,0,0,0,0,0,0,0];
  osums = [[0,0,0],[0,0,0],[0,0,0]];
  for (var i=0;i<9;i++){
    for (var j=0;j<9;j++){
      sumh[i] += board[i][j];
      sumv[j] += board[i][j];
      osums[Math.floor(i/3)][Math.floor(j/3)] += board[i][j];
    }
  }
  for (var i=0;i<3;i++) if (!osums[i].every(equals45)) return false;
  return (sumh.every(equals45) && sumv.every(equals45));
}
```