<!--yml
category: codewars
date: 2022-08-13 11:50:21
-->

# Codewars-KATA：Sudoku Solution Validator解题方法，Java实现_翎qian的博客-CSDN博客

> 来源：[https://blog.csdn.net/ROK_LI/article/details/121613873?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-121613873.nonecase](https://blog.csdn.net/ROK_LI/article/details/121613873?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-121613873.nonecase)

# Sudoku Solution Validator

## 题目

## 解题思路

1.  分两个循环，一个是分析行和列，一个是分析3*3的子网格
2.  分析行和列的比较简单，只需要判断map集合是否有重复的和该行或列属于1-9就ok了
3.  分析3*3的子网格比较麻烦，需要3个map集合，所以直接设置其取余为2就可以进行重置，其中的map集合判断与上述第一个循环的判断保持一致就ok了

## 代码

```
import java.util.HashMap;
import java.util.Map;

public class SudokuValidator {
    public static boolean check(int[][] sudoku) {
        Map<Integer,Integer> map1 = new HashMap<>();
        Map<Integer,Integer> map2 = new HashMap<>();
        Map<Integer,Integer> map3 = new HashMap<>();
        for(int i = 0; i < 9; i++){
            for(int j = 0; j < 9; j++){
                if(sudoku[i][j] < 1 || sudoku[i][j] > 9){
                    return false;
                }
                if(map1.containsKey(sudoku[i][j])){
                    return false;
                }else {
                    map1.put(sudoku[i][j],1);
                }
            }
            for(int j = 0; j < 9; j++){
                if(map2.containsKey(sudoku[j][i])){
                    return false;
                }else {
                    map2.put(sudoku[j][i],1);
                }
            }
            map1.clear();
            map2.clear();
        }
        for(int i = 0; i < 9; i++){
            if(i % 3 == 0){
                map1.clear();
                map2.clear();
                map3.clear();
            }
            for(int j = 0; j < 9; j++){
                if(j / 3 == 0){
                    if(map1.containsKey(sudoku[i][j])){
                        return false;
                    }else {
                        map1.put(sudoku[i][j],1);
                    }
                }
                if(j / 3 == 1){
                    if(map2.containsKey(sudoku[i][j])){
                        return false;
                    }else {
                        map2.put(sudoku[i][j],1);
                    }
                }
                if(j / 3 == 2){
                    if(map3.containsKey(sudoku[i][j])){
                        return false;
                    }else {
                        map3.put(sudoku[i][j],1);
                    }
                }
            }
        }
        return true;
    }
} 
```

```
 public static boolean check(int[][] sudoku) {
	        for (int i = 0; i < sudoku.length; i++) {
	            for (int j = 0; j < sudoku.length; j++) {
	                for (int i2 = 0; i2 < sudoku.length; i2++) {
	                    for (int j2 = 0; j2 < sudoku.length; j2++) {
	                        if(sudoku[i][j]==0)
	                            return false;
	                        if(i==i2 && j==j2)
	                            continue;
	                        if(sudoku[i][j]==sudoku[i2][j2])
	                            if (i/3==i2/3 && j/3==j2/3 || i==i2 || j==j2)
	                                return false;
	                    }
	                }
	            }
	        }
	        return true;
	    } 
```