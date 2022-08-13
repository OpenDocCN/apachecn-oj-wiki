<!--yml
category: codewars
date: 2022-08-13 11:43:41
-->

# codewars -- Sudoku Solver （python）_静看丶雨落时的博客-CSDN博客

> 来源：[https://blog.csdn.net/xiaopc3357/article/details/81284301?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-81284301.nonecase](https://blog.csdn.net/xiaopc3357/article/details/81284301?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-81284301.nonecase)

## codewars Sudoku Solver

### 难度系数：3kyu

###### 花了不少时间解决了一个较难题目，分享一下！

#### 题目：

Write a function that will solve a 9x9 Sudoku puzzle. The function will take one argument consisting of the 2D puzzle array, with the value 0 representing an unknown square.

The Sudokus tested against your function will be “easy” (i.e. determinable; there will be no need to assume and test possibilities on unknowns) and can be solved with a brute-force approach.

**For Sudoku rules, see the Wikipedia article.**

> puzzle = [[5,3,0,0,7,0,0,0,0],
> [6,0,0,1,9,5,0,0,0],
> [0,9,8,0,0,0,0,6,0],
> [8,0,0,0,6,0,0,0,3],
> [4,0,0,8,0,3,0,0,1],
> [7,0,0,0,2,0,0,0,6],
> [0,6,0,0,0,0,2,8,0],
> [0,0,0,4,1,9,0,0,5],
> [0,0,0,0,8,0,0,7,9]]

**sudoku(puzzle)**

> Should return
> [[5,3,4,6,7,8,9,1,2],
> [6,7,2,1,9,5,3,4,8],
> [1,9,8,3,4,2,5,6,7],
> [8,5,9,7,6,1,4,2,3],
> [4,2,6,8,5,3,7,9,1],
> [7,1,3,9,2,4,8,5,6],
> [9,6,1,5,3,7,2,8,4],
> [2,8,7,4,1,9,6,3,5],
> [3,4,5,2,8,6,1,7,9]]

#### 解题

本质为一个数独问题，先前做了很多弯路，一开始采用人为解题思路发现代码太难编写，因此参考了网上一些解析，但始终没找到**codewars**这道原题的python解法，实际上采用暴力循环，不断改变填充值，使其满足横竖，小3*3九宫格相互不同即可求解！！！
代码：

```
def sudoku(puzzle):
    def vaild(puzzle):
        for m in range(9):
            if puzzle[m][j]==puzzle[i][j] and m!= i:
                return False
        for n in range(9):
            if puzzle[i][n]==puzzle[i][j] and n!= j:
                return False
        for m in range(3):
            for n in range(3):
                if puzzle[int(i/3)*3+m][int(j/3)*3+n]==puzzle[i][j] and m!= i and n!= j and int(i/3)*3+m != i and int(j/3)*3+n!=j:
                    return False
        return True
    for i in range(9):
        for j in range(9):
            if puzzle[i][j] == 0:
                for d in range(1,10):
                    puzzle[i][j] = d
                    if vaild(puzzle):
                        if sudoku(puzzle):
                            return puzzle
                        else:
                            puzzle[i][j] = 0
                    else:
                        puzzle[i][j] = 0
                return False 
    return puzzle

puzzle = [[5,3,0,0,7,0,0,0,0],
          [6,0,0,1,9,5,0,0,0],
          [0,9,8,0,0,0,0,6,0],
          [8,0,0,0,6,0,0,0,3],
          [4,0,0,8,0,3,0,0,1],
          [7,0,0,0,2,0,0,0,6],
          [0,6,0,0,0,0,2,8,0],
          [0,0,0,4,1,9,0,0,5],
          [0,0,0,0,8,0,0,7,9]]
print (sudoku(puzzle))
```