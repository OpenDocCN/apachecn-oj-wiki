<!--yml
category: codewars
date: 2022-08-13 11:49:16
-->

# codewars练习（javascript）-2021/3/30_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/femalehacker/article/details/115317992?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-115317992.nonecase](https://blog.csdn.net/femalehacker/article/details/115317992?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-115317992.nonecase)

## codewars-js练习

### 2021/3/30

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【FIXME: Replace all dots】

**<mark>example</mark>**：

```
"one.two.three" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> var replaceDots = function(str) {
  		return str.replace(/[.]/g, '-');
	}

    console.log(replaceDots("one.two.three")); </script> 
```

#### 【2】<8kyu>【Reversed sequence】

**<mark>example</mark>**：

```
5 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> const reverseSeq = n => {
		var arr = [];
		for(var i=n;i>0;i--){
			arr.push(i);
		}
		return arr;
	};

    console.log(reverseSeq(5)); </script> 
```

#### 【3】<5kyu>【Scramblies】

如果str1的部分字符可以重新排列以匹配str2，则返回true，否则返回false

**<mark>example</mark>**：

```
scramble('rkqodlw', 'world') ==> True
scramble('cedewaraaossoqqyt', 'codewars') ==> True
scramble('katas', 'steak') ==> False 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function scramble(str1, str2) {
	    var arr1 = str1.split("").sort();
	    var arr2 = str2.split("").sort();
	    var i = 0;
	    for(var x = 0; i<arr2.length && x<=arr1.length; x++) {
	        if(arr2[i] === arr1[x]) {
	            i++;
	        }
	    }
	    return (x <= arr1.length);
	}

    console.log(scramble('rkqodlw','world'));

	console.log(scramble('katas','steak')); </script> 
```

```
function scramble(str1, str2) {
	    var count = Object.create(null);

	    Array.prototype.forEach.call(str1, function(a) {
	        count[a] = (count[a] || 0) + 1;
	    });

	    return Array.prototype.every.call(str2, function(a) {
	        return count[a]--;
	    });
	} 
```