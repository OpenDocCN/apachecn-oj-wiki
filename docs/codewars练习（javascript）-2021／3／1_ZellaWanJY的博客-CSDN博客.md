<!--yml
category: codewars
date: 2022-08-13 11:32:15
-->

# codewars练习（javascript）-2021/3/1_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/114251826?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-114251826.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/114251826?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-114251826.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/3/1

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Currying functions: multiply all elements in an array】

To complete this Kata you need to make a function `multiplyAll`/`multiply_all` which takes an array of integers as an argument. This function must return another function, which takes a single integer as an argument and returns a new array.

The returned array should consist of each of the elements from the first array multiplied by the integer.

即要创建两个函数

**<mark>example</mark>**：

```
multiplyAll([1, 2, 3])(2) = [2, 4, 6]; 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function multiplyAll(arr){
            return function (n){

                if(arr.length == 0)return [];
                let result = [];
                for(let i=0;i<arr.length;i++){
                    result.push(arr[i]*n);
                }
                return result;
            }

        }

        console.log(multiplyAll([1, 2, 3])(1));
        console.log(multiplyAll([1, 2, 3])(2));
        console.log(multiplyAll([])(10)); </script> 
```

#### 【2】<8kyu>【Is he gonna survive?】

each dragon takes 2 bullets to be defeated, our hero has no idea how many bullets he should carry.

**<mark>example</mark>**：

```
hero(10, 5)
hero(7, 4)
hero(100, 40)
hero(0,1) 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function hero(bullets, dragons){

            if(bullets < dragons*2)return false
            return true
        }

        console.log(hero(10, 5));
        console.log(hero(7, 4));
        console.log(hero(100, 40));
        console.log(hero(0,1)); </script> 
```

#### 【3】<6kyu>【A Cinema】

`b` boys and `g` girls went to the cinema and bought tickets for consecutive seats in the same row. Write a function that will tell you how to sit down for boys and girls, so that at least one girl sits next to each boy, and at least one boy sits next to each girl.

**<mark>example</mark>**：

```
cinema(1,1) === "BG" (the result like "GB" is also valid)
cinema(5,5) === "BGBGBGBGBG" (the result like "GBGBGBGBGB" is also valid)
cinema(5,3) === "BGBGBBGB" (the results like "BGBBGBBG" or "BGBBGBGB" and so on are also valid)
cinema(3,3) === "BGBGBG" (the result like "GBGBGB" is also valid)
cinema(100,3) === null 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function cinema(boys, girls) {
            if (boys > girls * 2 || girls > boys * 2) {
                return null;
            } else if (boys === girls) {
                return "".padStart(boys + girls, "BG");
            } else if (boys > girls) {
                return "BGB".repeat(boys - girls).padEnd(boys + girls, "GB");    
            }
                return "GBG".repeat(girls - boys).padEnd(boys + girls, "BG");    
        }

        console.log(cinema(1,1));
        console.log(cinema(5,5));
        console.log(cinema(5,3));
        console.log(cinema(100,3)); </script> 
```

**知识点**

`padStart()`用于头部补全，`padEnd()`用于尾部补全。

```
'x'.padStart(5, 'ab') 
'x'.padStart(4, 'ab') 
'x'.padEnd(5, 'ab') 
'x'.padEnd(4, 'ab') 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>
又是一个工作日