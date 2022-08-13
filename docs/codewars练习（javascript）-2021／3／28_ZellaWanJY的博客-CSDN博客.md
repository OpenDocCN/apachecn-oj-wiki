<!--yml
category: codewars
date: 2022-08-13 11:46:38
-->

# codewars练习（javascript）-2021/3/28_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/115277520?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-115277520.nonecase](https://blog.csdn.net/FemaleHacker/article/details/115277520?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-115277520.nonecase)

## codewars-js练习

### 2021/3/28

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Remove exclamation marks】

Write function RemoveExclamationMarks which removes all exclamation marks from a given string.

**<mark>example</mark>**：

```
"Hello World!" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function removeExclamationMarks(s) {
		return s.replace(/[!]/g,'')
	}

    console.log(removeExclamationMarks("Hello World!")); </script> 
```

#### 【2】<8kyu>【Convert number to reversed array of digits】

Given a random non-negative number, you have to return the digits of this number within an array in reverse order.

**<mark>example</mark>**：

```
348597 => [7,9,5,8,4,3] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function digitize(n) {
		return [...`${n}`].map(el => parseInt(el)).reverse()
	}

    console.log(digitize(348597)); </script> 
```

**<mark>知识点</mark>**

**js将数字转换为数字数组:**

```
const converToArray = number => [...`${number}`].map(el => parseInt(el))

converToArray(5678) 
converToArray(12345678) 
```