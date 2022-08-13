<!--yml
category: codewars
date: 2022-08-13 11:36:26
-->

# codewars练习（javascript）-2021/2/23_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/113973012?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-113973012.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/113973012?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-113973012.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/2/23

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<8kyu>【Reversed Strings】

Complete the solution so that it reverses the string passed into it.

**<mark>example</mark>**：

```
'world'  =>  'dlrow' 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function solution(str){
            return str.split('').reverse().join('')
        }

        console.log(solution('hello'));
        console.log(solution('')); </script> 
```

#### 【2】<6kyu>【Word search】

You are given a word `target` and list of sorted(by length(increasing), number of upper case letters(decreasing), natural order) unique words `words` which always contains `target`, your task is to find the index(0 based) of `target` in `words`,which would always be in the list.

您将得到一个单词目标和一个排序(按长度(增加)、大写字母数量(减少)、自然顺序)的唯一单词单词，这些单词总是包含target，您的任务是查找target在单词中的索引(基于0)，它总是在列表中。

**(列表按长度(从小到大)排序，然后按大写字母数量(最大到最小)，然后按自然顺序排序)**

**<mark>example</mark>**：

```
words = ['JaCk', 'Jack', 'jack', 'jackk', 'COdewars', 'codeWars', 'abcdefgh', 'codewars']
'''
(list is sorted by length(small to big), then by number of uppercase letters(maximum to minimum) and then by natural order)
'''
target = 'codewars'

words = ['cP', 'rE', 'sZ', 'am', 'bt', 'ev', 'hq', 'rx', 'yi', 'akC', 'nrcVpx', 'iKMVqsj']
target = 'akC' 
```

<mark>**solution**</mark>

**第一种 超出时间**

```
 function indexOf(words, target){

        } 
```

**第二种 超出时间**

```
 function indexOf(words, target){
            for(var i=0;i<words.length;i++){
                if(words[i]==target){
                    return i
                }
            }
        } 
```

**第三种 二分查找 pass**

```
<script type="text/javascript"> function indexOf (words, target) {

            let first = 0, last = words.length - 1;
            while (first < last) {
                let middle = parseInt((first + last) / 2);  
                if (words[middle].length < target.length) {
                    first = middle + 1;
                } else {
                    last = middle - 1;
                }
            }
            return words.indexOf(target, first);
        };

        console.log(indexOf(['JaCk', 'Jack', 'jack', 'jackk', 'COdewars', 'codeWars', 'abcdefgh', 'codewars'], 'codewars'));
        console.log(indexOf(['cP', 'rE', 'sZ', 'am', 'bt', 'ev', 'hq', 'rx', 'yi', 'akC', 'nrcVpx', 'iKMVqsj'], 'akC')); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>