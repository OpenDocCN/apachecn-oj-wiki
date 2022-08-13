<!--yml
category: codewars
date: 2022-08-13 11:50:42
-->

# codewars , js实现4kyu:Range Extraction_lxx-sissi的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_35438535/article/details/106207617?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-106207617.nonecase](https://blog.csdn.net/sinat_35438535/article/details/106207617?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-106207617.nonecase)

# 题目描述

该kata的链接地址: [link](https://www.codewars.com/kata/51ba717bb08c1cd60f00002f).

A format for expressing an ordered list of integers is to use a comma separated list of either

*   individual integers

*   or a range of integers denoted by the starting integer separated from the end integer in the range by a dash, ‘-’. The range includes all integers in the interval including both endpoints. It is not considered a range unless it spans at least 3 numbers. For example (“12, 13, 15-17”)
    Complete the solution so that it takes a list of integers in increasing order and returns a correctly formatted string in the range format.

# Example

```
solution([-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20]); 
```

# 代码实现

## 我完成的代码

```
function solution(list){

	 let newArr = [];
	 cal(list,i = 1);
	 function cal(list,i){
	        if(list.length > 0){  
	            (list[0] + i) == list[i] ? cal(list,i += 1) : newArr.push(list.splice(0,i));
	            cal(list,1);
	        }else{
	           return true;
	        }
	  }
	 return newArr.map(x => {
	       x.length > 2 && (x = `${x[0]}-${x[x.length-1]}`);
	       return x;
	  }).join(',');
} 
```

# 我的解题步骤

1.大体思路:先不管连续的数字是不是小于3,我要把所有的连续的数字都存在一个数组里 ,然后将这些数组构成一个二维数组,得出结果之后再处理这个二维数组得出最后的结果;

2.怎么样把所有的连续的字符都存起来呢?

每次从`list[0]`开始,检测`list[0]+1`等不等于`list[1]`,等于的话,检测`list[0]+2`等不等于`list[2]`,等于的话,检测`list[0]+3`等不等于`list[3]`…(这里为了熟悉递归,我用了递归来计算等于的情况,当然也可以用别的方法)

对应`(list[0] + i) == list[i] ? cal(list,i += 1) : newArr.push(list.splice(0,i));` `true`的情况;

一直到不等于的时候,`list`数组删除从0位置的开始长度为i字符,并将删除的字符存到`newArr`里,然后重新从`list[0]`开始查找,

对应`(list[0] + i) == list[i] ? cal(list,i += 1) : newArr.push(list.splice(0,i));` `false`的情况.
直到`list`数组为空,我就得到了想要的那个二维数组;

3.处理二维数组,遍历该二维数组,当子数组x有长度大于2的时候,让这个数组x等于 `x[0] - x[x.length-1]`(这里使用了es6的写法`${x[0]}-${x[x.length-1]}`),最后将newArr以,分隔为字符串

# 我认为的难点