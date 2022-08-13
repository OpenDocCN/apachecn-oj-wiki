<!--yml
category: codewars
date: 2022-08-13 11:34:41
-->

# codewars练习（javascript）-2021/1/30_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113419904?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-113419904.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/113419904?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-113419904.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/1/30

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Check the exam】

The first input array is the key to the correct answers to an exam, like [“a”, “a”, “b”, “d”]. The second one contains a student’s submitted answers.

The two arrays are not empty and are the same length. Return the score for this array of answers, giving +4 for each correct answer, -1 for each incorrect answer, and +0 for each blank answer, represented as an empty string (in C the space character is used).

If the score < 0, return 0.

**<mark>example</mark>**：

```
checkExam(["a", "a", "b", "b"], ["a", "c", "b", "d"]) → 6
checkExam(["a", "a", "c", "b"], ["a", "a", "b",  ""]) → 7
checkExam(["a", "a", "b", "c"], ["a", "a", "b", "c"]) → 16
checkExam(["b", "c", "b", "a"], ["",  "a", "a", "c"]) → 0 
```

<mark>**solution**</mark>

```
 <script type="text/javascript"> function checkExam(array1, array2) {

 			var correct = 0;
 			var error = 0;
 			var other = 0;
 			for(var i=0;i<array1.length;i++){
 				if(array1[i] == array2[i]){
 					correct ++;
 				}else if(array2[i] == ''){
 					other = 0;
 				}else{
 					error ++;
 				}
 			}

 			var result = correct * 4 + error * (-1) + other;
 			if(result <0){
 				return 0;
 			}
 			return result;
 		}

		验证
		console.log(checkExam(["a", "a", "b", "b"], ["a", "c", "b", "d"]));
		console.log(checkExam(["a", "a", "c", "b"], ["a", "a", "b",  ""]));
		console.log(checkExam(["b", "c", "b", "a"], ["",  "a", "a", "c"])); </script> 
```

#### 【2】<7kyu>【Love vs friendship】

If　`a = 1, b = 2, c = 3 ... z = 26`

Then `l + o + v + e = 54`

and `f + r + i + e + n + d + s + h + i + p = 108`

So `friendship` is twice stronger than `love` 😃

The input will always be in lowercase and never be empty.

**<mark>example</mark>**：

```
wordsToMarks("attitude")
wordsToMarks("friends") 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function wordsToMarks(string){
 			var arr = [];
 			var count = 0;
 			for(var i=0;i<string.length;i++){

 				var temp = string.substring(i,i+1).charCodeAt()-96;
 				arr.push(temp);
 			}

 			for(var j=0;j<arr.length;j++){
 				count += arr[j];
 			}
 			return count;
 		}

		console.log(wordsToMarks("attitude"));
		console.log(wordsToMarks("friends")); </script> 
```

#### 【3】<7kyu>【Remove anchor from URL】

Complete the function/method so that it returns the url with anything after the anchor (`#`) removed.

**<mark>example</mark>**：

```
 removeUrlAnchor('www.codewars.com#about')

removeUrlAnchor('www.codewars.com?page=1') 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function removeUrlAnchor(url){
 			var index = url.indexOf('#');

 			if(index !=-1){
 				 url = url.substring(0,index);
 			}
 			return url;
 		}

		console.log(removeUrlAnchor("www.codewars.com#about"));
		console.log(removeUrlAnchor("www.codewars.com?page=1")); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>