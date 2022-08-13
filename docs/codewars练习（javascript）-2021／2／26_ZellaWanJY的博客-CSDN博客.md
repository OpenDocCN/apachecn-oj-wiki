<!--yml
category: codewars
date: 2022-08-13 11:33:25
-->

# codewars练习（javascript）-2021/2/26_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/114115356?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-114115356.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/114115356?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-114115356.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/2/26

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Function 1 - hello world】

输出 ‘hello world!’

<mark>**solution**</mark>

```
<script type="text/javascript"> function greet(){
            return 'hello world!'

        }

        console.log(greet()); </script> 
```

#### 【2】<8kyu>【MakeUpperCase】

Write a function which converts the input string to uppercase.

<mark>**solution**</mark>

```
<script type="text/javascript"> function makeUpperCase(str) {
            return str.toUpperCase()
        }

        console.log(makeUpperCase("hello")); </script> 
```

#### 【3】<6kyu>【Easy Balance Checking】

**<mark>example</mark>**：

```
"1000.00
125 Market 125.45
126 Hardware 34.95
127 Video 7.45
128 Book 14.32
129 Gasoline 16.10"

输出:
"Original_Balance:_1000.00
125_Market_125.45_Balance_874.55
126_Hardware_34.95_Balance_839.60
127_Video_7.45_Balance_832.15
128_Book_14.32_Balance_817.83
129_Gasoline_16.10_Balance_801.73
Total_expense__198.27
Average_expense__39.65" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function balance(book) {
            let totalExpense = 0
                , [ originalBalance, ...entries ] = book
                .trim()
                .replace(/[^a-z0-9\s.]+/gi, '')
                .replace(/\s{2,}/g, m => m[0])
                .split(/\n/);

            originalBalance = parseFloat(originalBalance);

            entries = entries.map(row => 
                    row.replace(/\S+$/g, m => {
                        totalExpense += parseFloat(m);
                        return parseFloat(m).toFixed(2) + ' Balance ' + (originalBalance - totalExpense).toFixed(2);
                        })
                    );

            entries.unshift('Original Balance: ' + originalBalance.toFixed(2));
            entries.push('Total expense  ' + totalExpense.toFixed(2));
            entries.push('Average expense  ' + (totalExpense / (entries.length - 2)).toFixed(2));
            return entries.join("\r\n");

        } </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。 最后一题真是想好了好久</mark>