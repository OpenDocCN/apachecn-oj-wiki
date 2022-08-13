<!--yml
category: codewars
date: 2022-08-13 11:37:30
-->

# codewars练习（javascript）-2021/2/16_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113826003?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-113826003.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/113826003?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-113826003.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/2/16

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Transportation on vacation】

Every day you rent the car costs $40\. If you rent the car for 7 or more days, you get $50 off your total. Alternatively, if you rent the car for 3 or more days, you get $20 off your total.

**Write a code that gives out the total amount for different days(d).**

你租这辆车每天要花40美元。如果你租车7天或更长时间，你可以得到50美元的折扣。或者，如果你租车3天以上，你可以得到20美元的折扣

**<mark>example</mark>**：

```
rentalCarCost(1), 40)
rentalCarCost(2), 80)
rentalCarCost(5), 180)
rentalCarCost(10), 350) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function rentalCarCost(d) {

 			if(d >=7){
 				return (d*40)-50;
 			}else if(d >= 3 && d <7){
 				return (d*40)-20;
 			}else{
 				return d*40;
 			}
 		}

		console.log(rentalCarCost(1));
		console.log(rentalCarCost(10));
		console.log(rentalCarCost(5));
		console.log(rentalCarCost(3)); </script> 
```

#### 【2】<8kyu>【Century From Year】

The first century spans from the **year 1** *up to* and **including the year 100**, **The second** - *from the year 101 up to and including the year 200*, etc.

Given a year, return the century it is in.

**第一个世纪从公元1年到公元100年，第二，从公元101年到公元200年，等等。**

**<mark>example</mark>**：

```
centuryFromYear(1705)  returns (18)
centuryFromYear(1900)  returns (19)
centuryFromYear(1601)  returns (17)
centuryFromYear(2000)  returns (20) 
```

<mark>**solution**</mark>

```
 <script type="text/javascript"> function century(year) {

 			return Math.ceil(year/100);
 		}

		console.log(century(1705));
		console.log(century(1900));
		console.log(century(1601));
		console.log(century(2000));
		console.log(century(89)); </script> 
```

#### 【3】<8kyu>【Function 3 - multiplying two numbers】

Implement a function which multiplies two numbers.

**<mark>example</mark>**：

```
2*3 = 6 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function multiply(a,b){
 			return a*b;
 		}

		console.log(multiply(2, 3)); </script> 
```

#### 【4】<8kyu>【Filter out the geese】

Write a function, `gooseFilter`/`goose_filter`/`GooseFilter`, that takes an array of strings as an argument and returns a filtered array containing the same elements but with the ‘geese’ removed.

The geese are any strings in the following array, which is pre-populated in your solution:

```
 var geese = ["African", "Roman Tufted", "Toulouse", "Pilgrim", "Steinbache"]; 
```

**编写一个函数gooseFilter/goose_filter/ gooseFilter，它接受一个字符串数组作为参数，并返回一个过滤后的数组，该数组包含相同的元素，但去掉了’geese’。**

**<mark>example</mark>**：

```
["Mallard", "Hook Bill", "African", "Crested", "Pilgrim", "Toulouse", "Blue Swedish"] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function gooseFilter (birds) {
  			var geese = ["African", "Roman Tufted", "Toulouse", "Pilgrim", "Steinbacher"];

  			for(var i=0;i<birds.length;i++){
  				for(var j=0;j<geese.length;j++){
  					if(birds[i] == geese[j]){
  						birds.splice(i,1);
  						i=i-1;
  					}
  				}
  			}
  			return birds;

		};

		console.log(gooseFilter(["Mallard", "Hook Bill", "African", "Crested", "Pilgrim", "Toulouse", "Blue Swedish"])); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>