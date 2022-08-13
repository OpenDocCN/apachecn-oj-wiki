<!--yml
category: codewars
date: 2022-08-13 11:37:40
-->

# （Codewars）Your order, please_e黑子的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41801219/article/details/116426838?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-116426838-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_41801219/article/details/116426838?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-116426838-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# Your order, please

## 您的任务是对给定的字符串进行排序。字符串中的每个单词都将包含一个数字。该数字是单词在结果中应具有的位置。

注意：数字可以从1到9。因此1将是第一个单词（而不是0）。

如果输入字符串为空，则返回一个空字符串。输入字符串中的单词将仅包含有效的连续数字。

> ```
> function order(words){
>   
>     var words_spli = words.split(" ");
>     var obj= {}
>     var arr = words.match(/\d/g)
>     for(let i=0;i<words_spli.length;i++){
>                 
>                 
>                 
>                 
>                 obj[arr[i]] = words_spli[i]
>     }
>     var result =[];
>     
>     for (var key in obj) {
>         result.push(obj[key])
>     }
>       
>   return result.join(" ")
> } 
> ```
> 
> > Codewars上排名第一的答案
> 
> ```
>  return words.split(' ').sort(function(a, b){
>       return a.match(/\d/) - b.match(/\d/);
>    }).join(' '); 
> ```