<!--yml
category: codewars
date: 2022-08-13 11:46:30
-->

# codewars练习（javascript）-2021/2/1_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113504796?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-113504796.nonecase](https://blog.csdn.net/FemaleHacker/article/details/113504796?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-113504796.nonecase)

## codewars-js练习

### 2021/2/1

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Anagram Detection】

An **anagram** is the result of rearranging the letters of a word to produce a new word (see [wikipedia](https://en.wikipedia.org/wiki/Anagram)).

**Note:** anagrams are case insensitive

Complete the function to return `true` if the two arguments given are anagrams of each other; return `false` otherwise.

**字谜是将一个单词的字母重新排列以产生一个新单词的结果。注意:字谜不区分大小写。如果给定的两个参数是彼此的字谜，则完成函数返回true;否则返回false。**

**<mark>example</mark>**：

```
"foefet" is an anagram of "toffee"

"Buckethead" is an anagram of "DeathCubeK" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> var isAnagram = function(test, original) {

			var tStr = test.toLowerCase().split('').sort().join('');
			var oStr = original.toLowerCase().split('').sort().join('');
			console.log(tStr,oStr);
			if(oStr===tStr){
				return true;
			}
			return false;
		};

		console.log(isAnagram("foefet", "toffee"));
		console.log(isAnagram("Twoo", "WooT"));
		console.log(isAnagram("dumble", "bumble"));
		console.log(isAnagram("ound", "round"));
		console.log(isAnagram("Buckethead", "DeathCubeK"));
		console.log(isAnagram("apple", "pale")); </script> 
```

#### 【2】<7kyu>【Round up to the next multiple of 5】

Given an integer as input, can you round it to the next (meaning, “higher”) multiple of 5?

**四舍五入到下一个5的倍数**

**<mark>example</mark>**：

```
input:    output:
0    ->   0
2    ->   5
3    ->   5
12   ->   15
21   ->   25
30   ->   30
-2   ->   0
-5   ->   -5
etc. 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function roundToNext5(n){
 			console.log('n',n);
 			if(n %5 !=0){
 				return (Math.floor(n/5)+1)*5;
 			}
 			return n;
 		}

		[
		  [0,0],
		  [1,5],
		  [3,5],
		  [5,5],
		  [7,10],
		  [39,40],
		  [-2,0],
		  [-5,-5]
		].forEach(
		  ([x,out])=> console.log(roundToNext5(x), out)
		); </script> 
```

#### 【3】<7kyu>【Mumbling】

**<mark>example</mark>**：

```
accum("abcd") -> "A-Bb-Ccc-Dddd"
accum("RqaEzty") -> "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
accum("cwAt") -> "C-Ww-Aaa-Tttt" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function accum(s) {

 			var result = [s[0]];
 			for(var i=1;i<s.length;i++){
 				var ss = s[i].toUpperCase() + new Array(i+1).join(s[i].toLowerCase());

 				result.push(ss);
 			}
 			return result.join('-');
 		}

		console.log(accum("ZpglnRxqenU")); </script> 
```

**知识点：重复n次**

```
function repeatString(str,n) {
	return new Array(n+1).join(str);
}
repeatString("a",3) 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>