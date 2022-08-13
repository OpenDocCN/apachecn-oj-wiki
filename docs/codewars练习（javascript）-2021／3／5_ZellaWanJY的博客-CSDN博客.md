<!--yml
category: codewars
date: 2022-08-13 11:39:14
-->

# codewars练习（javascript）-2021/3/5_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/114396304?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-20-114396304-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/FemaleHacker/article/details/114396304?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-20-114396304-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## codewars-js练习

### 2021/3/5

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<7kyu>【Convert an array of strings to array of numbers】

**<mark>example</mark>**：

```
["1", "2", "3"] 
["1.1","2.2","3.3"] 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function toNumberArray(stringarray){

            var result = [];
            for(var i=0;i<stringarray.length;i++){
                if(stringarray[i]%1 ==0){
                    result.push(parseInt(stringarray[i]))
                }else{
                    result.push(parseFloat(stringarray[i]))
                }
            }
            return result
        }

        console.log(toNumberArray(["1.1","2.2","3.3"]));
        console.log(toNumberArray(['1','2','3'])) </script> 
```

#### 【2】<7kyu>【Nth Root of a Number】

**<mark>example</mark>**：

```
Input: x=4, n=2, output: 2. The square root of 4 is 2, 2^2 = 4
Input: x=8, n=3, output: 2. The cube root of 8 is 2 , 2^3 = 8
Input: x=256, n=4, output: 4. The 4th root of 256 is 4 , 4^4 = 256
Input: x=9, n=2, output: 3. The square root of 9 is 3 , 3^2 = 9
Input: x=6.25, n=2, output: 2.5. The square root of 6.25 is 2.5 , 2.5^2 = 6.25 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function root(x,n) {

            return Math.pow(x, 1/n)
        }

        console.log(root(4,2));
        console.log(root(256,4)); </script> 
```

#### 【3】<6kyu>【Roman Numerals Decoder】

```
So 1990 is rendered "MCMXC" (1000 = M, 900 = CM, 90 = XC) and 2008 is rendered "MMVIII" (2000 = MM, 8 = VIII). The Roman numeral for 1666, "MDCLXVI", uses each letter in descending order.
Symbol    Value
I          1
V          5
X          10
L          50
C          100
D          500
M          1,000 
```

**<mark>example</mark>**：

```
solution('XXI'); 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function solution(roman){
            console.log(roman)
            var value = {'I':1,'V':5,'X':10,'L':50,'C':100,'D':500,'M':1000};
            var arr = roman.split('');
            var sum =0;
            for(var i=0;i<arr.length;i++){
                if (i>0 && value[arr[i]]>value[arr[i-1]]){
                    sum = sum - 2*value[arr[i-1]]
                }
                sum += value[arr[i]];
            }
            return sum
        } 

        console.log(solution('IV')); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>