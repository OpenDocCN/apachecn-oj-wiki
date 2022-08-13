<!--yml
category: codewars
date: 2022-08-13 11:49:14
-->

# codewars练习（javascript）-2021/2/10_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113781918?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-113781918.nonecase](https://blog.csdn.net/FemaleHacker/article/details/113781918?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-113781918.nonecase)

## codewars-js练习

### 2021/2/10

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Hells Kitchen】

Obviously the words should be Caps, Every word should end with ‘!!!’, Any letter ‘a’ or ‘A’ should become ‘@’, Any other vowel should become ‘*’.

**这些单词应该是大写的，每个单词都应该以“!!!”结尾’，任何字母’a’或’A’应该变成’@’，任何其他元音应该变成’*’。**

**<mark>example</mark>**：

```
gordon('What feck damn cake'), 'WH@T!!!! F*CK!!!! D@MN!!!! C@K*!!!!'
gordon('are you stu pid'), '@R*!!!! Y**!!!! ST*!!!! P*D!!!!' 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function gordon(a){

 			var aU = a.toUpperCase();
 			var temp = aU.replace(/[aA]/g,'@').replace(/[AEIOU]/g,'*').split(' ');
 			for(var i=0;i<temp.length;i++){
 				temp[i] += '!!!!';
 			}
 			var result = temp.join(' ');

 			return result;
 		}

		console.log(gordon('What feck damn cake'));
		console.log(gordon('are you stu pid')); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>