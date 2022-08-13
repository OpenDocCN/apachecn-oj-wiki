<!--yml
category: codewars
date: 2022-08-13 11:51:17
-->

# [CodeWars]Matrix Determinant_Z Chelsea的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_51047199/article/details/120593038?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-120593038.nonecase](https://blog.csdn.net/weixin_51047199/article/details/120593038?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-120593038.nonecase)

# CodeWars里的4kyu题目Matrix Determinant

## 题目说明：

### Description:

Write a function that accepts a square matrix (N x N 2D array) and returns the determinant of the matrix.

How to take the determinant of a matrix – it is simplest to start with the smallest cases:

A 1x1 matrix |a| has determinant a.

A 2x2 matrix [ [a, b], [c, d] ] or

|a b|
|c d|
has determinant: a*d - b*c.

The determinant of an n x n sized matrix is calculated by reducing the problem to the calculation of the determinants of n matrices ofn-1 x n-1 size.

For the 3x3 case, [ [a, b, c], [d, e, f], [g, h, i] ] or

|a b c|
|d e f|
|g h i|
the determinant is: a * det(a_minor) - b * det(b_minor) + c * det(c_minor) where det(a_minor) refers to taking the determinant of the 2x2 matrix created by crossing out the row and column in which the element a occurs:

|- - -|
|- e f|
|- h i|
Note the alternation of signs.

The determinant of larger matrices are calculated analogously, e.g. if M is a 4x4 matrix with first row [a, b, c, d], then:

det(M) = a * det(a_minor) - b * det(b_minor) + c * det(c_minor) - d * det(d_minor)

## Python解决方案：

使用numpy模块中的linalg.det() 函数进行计算矩阵的行列式的值，最通过round（）函数对数值进行四舍五入计算。

```
def determinant(matrix):
    import numpy as np
    m = np.mat(matrix)
    c = np.linalg.det(m)
    c = int(round(c))
    return c 
```