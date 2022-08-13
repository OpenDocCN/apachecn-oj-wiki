<!--yml
category: codewars
date: 2022-08-13 11:48:01
-->

# codewars , js实现4kyu:Square into Squares. Protect trees!_lxx-sissi的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_35438535/article/details/106113942?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-106113942.nonecase](https://blog.csdn.net/sinat_35438535/article/details/106113942?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-106113942.nonecase)

# 4kyu:Square into Squares. Protect trees!

My little sister came back home from school with the following task: given a squared sheet of paper she has to cut it in pieces which, when assembled, give squares the sides of which form an increasing sequence of numbers. At the beginning it was lot of fun but little by little we were tired of seeing the pile of torn paper. So we decided to write a program that could help us and protects trees.

## Task

Given a positive integral number n, return a strictly increasing sequence (list/array/string depending on the language) of numbers, so that the sum of the squares is equal to n².

If there are multiple solutions (and there will be), return as far as possible the result with the largest possible values:

## Examples

decompose(11) must return [1,2,4,10]. Note that there are actually two ways to decompose 11², 11² = 121 = 1 + 4 + 16 + 100 = 1² + 2² + 4² + 10² but don’t return [2,6,9], since 9 is smaller than 10.

For decompose(50) don’t return [1, 1, 4, 9, 49] but [1, 3, 5, 8, 49] since [1, 1, 4, 9, 49] doesn’t form a strictly increasing sequence.

## Note

Neither [n] nor [1,1,1,…,1] are valid solutions. If no valid solution exists, return nil, null, Nothing, None (depending on the language) or “[]” © ,{} (C++), [] (Swift, Go).

The function “decompose” will take a positive integer n and return the decomposition of N = n² as:

[x1 … xk] or
“x1 … xk” or
Just [x1 … xk] or
Some [x1 … xk] or
{x1 … xk} or
“[x1,x2, … ,xk]”
depending on the language (see “Sample tests”)

## Note for Bash

decompose 50 returns “1,3,5,8,49”
decompose 4 returns “Nothing”

## Hint

Very often xk will be n-1.

## js代码实现

```
function decompose(n) {

       var arr = [];
	   function equal(d,num){
	    	if (d < 0){return false}
	      else if (d == 0){return true}
	        for (var i = num - 1 ; i > 0 ; i--) {
	        	sum = equal(d - Math.pow(i,2), i)
	        	 if (sum){
	        	 	arr.push(i)
	                return arr 
	        	 }
	        }
	        	 return null
	    }
	   return equal(n*n,n)
} 
```