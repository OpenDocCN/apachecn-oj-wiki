<!--yml
category: codewars
date: 2022-08-13 11:39:21
-->

# codewars练习（javascript）-2021/4/252628_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/116124216?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-23-116124216-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/116124216?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-23-116124216-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/4/25

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<6kyu>【Twisted Sum】

**<mark>example</mark>**：

```
 1 + 2 + 3 + 4 = 10

1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + (1 + 0) = 46

1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + (1 + 0) + (1 + 1) + (1 + 2) = 51 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function twistedSum(n) {

		var sum = 0;
		for(var i=1;i<=n;i++){
			if(i>9){
				sum += parseInt(otherSum(i))
			}else{
				sum += i;
			}
		}
		return sum;
	}
	function otherSum(n){
		return  eval(n.toString().split('').join("+"))
	}

	console.log(twistedSum(3));
	console.log(twistedSum(10));
	console.log(twistedSum(11));
	console.log(twistedSum(12)); </script> 
```

#### 【2】<6kyu>【Most profit from stock quotes】

股票报价按日期顺序存储在一个数组中。股票利润是买卖股票时的价格差。每天，你可以买一单位股票，卖出你已经买的任何数量的股票，或者什么都不做。因此，最大的利润是在一个股票价格序列中所有对的最大差异。

**<mark>example</mark>**：

```
[ 1, 2, 3, 4, 5, 6]   => 15  (buy at 1,2,3,4,5 and then sell all at 6)
[ 6, 5, 4, 3, 2, 1]   => 0   (nothing to buy)
[ 1, 6, 5, 10, 8, 7] => 18  (buy at 1,6,5 and sell all at 10) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function getMostProfitFromStockQuotes(quotes) {
		console.log(quotes)
		var p = 0
		var max = quotes[quotes.length-1]
		for(let i =  quotes.length - 2; i >= 0; i--)
		{
			max = Math.max(max,quotes[i])

			if(quotes[i] < max)
			p+= max-quotes[i]
		}
		return p
	}

	console.log(getMostProfitFromStockQuotes([ 1, 2, 3, 4, 5, 6 ]));
    console.log(getMostProfitFromStockQuotes([ 6, 5, 4, 3, 2, 1 ]));
    console.log(getMostProfitFromStockQuotes([ 1, 6, 5, 10, 8, 7 ])); </script> 
```

### 2021/4/26

#### 【1】<6kyu>【Backspaces in string】

假设"#“类似于字符串中的退格符。这意味着字符串"a#bc#d"实际上是"bd”

有点类似于进栈出栈。

**<mark>example</mark>**：

```
"abc#d##c"      ==>  "ac"
"abc##d######"  ==>  ""
"#######"       ==>  ""
""              ==>  "" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function cleanString(s) {
		console.log(s)
		var arr = s.split('');
		var result = [];
		for(var i=0;i<arr.length;i++){
			if(arr[i] == '#'){
				result.pop()
			}else{
				result.push(arr[i]);
			}
		}
		return result.join('');
	} </script> 
```

#### 【2】<6kyu>【Binaries】

对于n的每一位d 【1】设k为d的位数【2】写k-1乘以数字0，再加上数字1【3】将数字d写成二进制字符串，最右边的位是最低位【4】连接【2】和【3】的结果，得到d的编码

**<mark>也就是每一位转换到的二进制数相连接。</mark>**

**<mark>example</mark>**：

```
code("77338855") --> "001111001111011101110001100000011000001101001101"
code("77338")  --> "0011110011110111011100011000"
code("0011121314") --> "1010111111011011011111001100"

decode("001111001111011101110001100000011000001101001101") -> "77338855"
decode("0011110011110111011100011000") -> "77338"
decode("1010111111011011011111001100") -> "0011121314" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> var C = ['10', '11', '0110', '0111', '001100', '001101', '001110', '001111', '00011000', '00011001'];

	function code(strng) {
		console.log(strng)
		var r='';
		for (c of strng){
			r += C[c];
		}
		return r;
	}
	function decode(str) {
		var r='';
		while(str){
			for (var l of [2, 4, 6, 8]){
				c = str.slice(0, l);
				if (C.includes(c)){
					r+=C.indexOf(c)
					str = str.slice(l)
				}
			}
		}
		return r
	}

	console.log(code("62"));
	console.log(decode("10001111")); </script> 
```

### 2021/4/28

#### 【1】<7kyu>【Find the vowels】

我们想知道给定单词中元音的索引，例如，单词super中有两个元音(第二个和第四个字母)。

**<mark>example</mark>**：

```
Mmmm  => []
Super => [2,4]
Apple => [1,5]
YoMama -> [1,2,4,6] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function vowelIndices(word){
		console.log(word)
		var arr = []
		for(var i = 0; i < word.length; i++) {
			if(/[aeioyu]/i.test(word[i])) {
				arr.push(i+1);
			}
		}
		return arr
	}

	console.log(vowelIndices("mmm"));
	console.log(vowelIndices("supercalifragilisticexpialidocious")); </script> 
```