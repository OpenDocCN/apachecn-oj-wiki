<!--yml
category: codewars
date: 2022-08-13 11:39:02
-->

# codewars练习（javascript）-2021/3/31_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/115341990?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-14-115341990-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/115341990?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-14-115341990-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/3/31

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Counting sheep】

**<mark>example</mark>**：

```
[true,  true,  true,  false,
  true,  true,  true,  true ,
  true,  false, true,  false,
  true,  false, false, true ,
  true,  true,  true,  true ,
  false, false, true,  true] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function countSheeps(arrayOfSheep) {
		console.log(arrayOfSheep)
		var str = arrayOfSheep.join('');
		var arr = str.match(/true/gi);
		console.log(arr==null)
		return arr!=null?arr.length:0;
	}

    array1 = [true,  true,  true,  false,
              true,  true,  true,  true ,
              true,  false, true,  false,
              true,  false, false, true ,
              true,  true,  true,  true ,
              false, false, true,  true ];
   	array2 = [null,null,null,null,null,null,null]

    console.log(countSheeps(array1));
    console.log(countSheeps(array2)); </script> 
```

#### 【2】<5kyu>【Pete, the baker】

编写一个函数cakes()，该函数接受配方(对象)和可用的配料(也是一个对象)，并返回Pete可以烘烤的蛋糕的最大数量(整数)

**<mark>example</mark>**：

```
 cakes({flour: 500, sugar: 200, eggs: 1}, {flour: 1200, sugar: 1200, eggs: 5, milk: 200}); 

cakes({apples: 3, flour: 300, sugar: 150, milk: 100, oil: 100}, {sugar: 500, flour: 2000, milk: 2000}); 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function cakes(recipe, available) {

		var arr = [];
		for(var i in recipe){

			if(i in available){
				arr.push(Math.floor(available[i]/recipe[i]))
			}
			else return 0
		}
		return Math.min(...arr)
	}

    recipe = {flour: 500, sugar: 200, eggs: 1};
    available = {flour: 1200, sugar: 1200, eggs: 5, milk: 200};
    console.log(cakes(recipe, available));

    recipe = {apples: 3, flour: 300, sugar: 150, milk: 100, oil: 100};
    available = {sugar: 500, flour: 2000, milk: 2000};
    console.log(cakes(recipe, available)); </script> 
```