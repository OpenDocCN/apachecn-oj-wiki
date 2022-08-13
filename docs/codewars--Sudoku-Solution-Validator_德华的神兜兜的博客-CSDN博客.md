<!--yml
category: codewars
date: 2022-08-13 11:51:19
-->

# codewars -Sudoku Solution Validator_德华的神兜兜的博客-CSDN博客

> 来源：[https://blog.csdn.net/anbncn1234/article/details/104681225?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-104681225.nonecase](https://blog.csdn.net/anbncn1234/article/details/104681225?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-104681225.nonecase)

codewars -Sudoku Solution Validator

我的代码：

```
def valid_solution(board):
    error_cnt = 0
    for x in board:

        if (1 in x) and (2 in x) and (3 in x) and (4 in x) and (5 in x) and (6 in x) and (7 in x) and (8 in x) and (9 in x):
            continue
        else:
            error_cnt += 1
    for i in range(0,9):
        buffer = []
        for j in range(0,9):
            buffer.append(board[j][i])
        if (1 in buffer) and (2 in buffer) and (3 in buffer) and (4 in buffer) and (5 in buffer) and (6 in buffer) and (7 in buffer) and (8 in buffer) and (9 in buffer):
            continue
        else:
            error_cnt += 1

    for m in range(0,3):
        for n in range(0,3):
            buffer1 = []
            for row in range(0,3):
                for col in range(0,3):
                    buffer1.append(board[m*3 + row][n*3 + col])
            print(buffer1)
            if (1 in buffer1) and (2 in buffer1) and (3 in buffer1) and (4 in buffer1) and (5 in buffer1) and (
                    6 in buffer1) and (7 in buffer1) and (8 in buffer1) and (9 in buffer1):
                continue
            else:
                error_cnt += 1

    print(error_cnt)
    if error_cnt> 0:
        return False
    else:
        return True 
```