<!--yml
category: codewars
date: 2022-08-13 11:40:33
-->

# 【Codewars】＜3kyu＞Calculator_cbat01的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_36270908/article/details/111543465?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-22-111543465-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_36270908/article/details/111543465?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-22-111543465-null-null.142^v40^control,185^v2^control&utm_term=codewars)

### 题目:

> Create a simple calculator that given a string of operators (), +, -, *, / and numbers separated by spaces returns the value of that expression
> **这个题目要我们实现一个简单的计算器，计算出带加减乘除的字符串运算后的值。**

### 例子:

```
Calculator().evaluate("2 / 2 + 3 * 4 - 6") # => 7 
```

### 题解一:

```
 const Calculator = function() {
    this.evaluate = string => {

        var arr = string.split(' ');

        for(let i=0;i<arr.length;i++){
            if(arr[i] === '*'){
                arr[i+1] = arr[i-1] * arr[i+1]
                arr.splice(i-1,2)
                i=i-2;
            }else if(arr[i] === '/'){
                arr[i+1] = arr[i-1] / arr[i+1]
                arr.splice(i-1,2)
                i=i-2;
            }
        }

        for(let i=0;i<arr.length;i++){
            if(arr[i] === '+'){
                arr[i+1] = parseFloat(arr[i-1]) + parseFloat(arr[i+1])
                arr.splice(i-1,2)
                i=i-2;
            }else if(arr[i] === '-'){
                arr[i+1] = arr[i-1] - arr[i+1]
                arr.splice(i-1,2)
                i=i-2;
            }
        }
        return arr.join("");
    }
}; 
```

### 题解二:

```
 const Calculator = function() {
    this.operation = (a, b, operator) => {
      switch (operator) {
        case '+': return a + b;
        case '-': return a - b;
        case '*': return a * b;
        case '/': return a / b;
      }
    }

    this.evaluate = (str) => {
        const args = str.split(' ');
        ['/', '*', '-', '+'].forEach((op) => {
            while ((i = args.indexOf(op)) !== -1) {
                args[i - 1] = this.operation(+args[i - 1], +args[i + 1], op);
                args.splice(i, 2);
            }
        })
        return +args[0];
    }
}; 
```