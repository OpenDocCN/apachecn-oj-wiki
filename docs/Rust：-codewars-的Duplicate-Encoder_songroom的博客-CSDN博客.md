<!--yml
category: codewars
date: 2022-08-13 11:49:03
-->

# Rust: codewars 的Duplicate Encoder_songroom的博客-CSDN博客

> 来源：[https://blog.csdn.net/wowotuo/article/details/78141720?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-78141720.nonecase](https://blog.csdn.net/wowotuo/article/details/78141720?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-78141720.nonecase)

题目如下：

[https://www.codewars.com/kata/duplicate-encoder/rust](https://www.codewars.com/kata/duplicate-encoder/rust)

Examples:

“din” => “(((“

“recede” => “()()()”

“Success” => “)())())”

“(( @” => “))((“

简单来说：
（1）对于其中字符出现次数>1的，字符变成“）”，否则为“（”；
（2）不区分大小写。

一、我的解法

```
fn duplicate_encode(word:&str)->String {
   let mut strs ="".to_string()
   let chars= word.to_lowercase().chars().into_iter().collect::<Vec<char>>()
   (&chars).into_iter().map(|&x| 
   {
       match (&chars).into_iter().filter(|&s|*s==x).count()>1usize{
          true=> strs.push(')'),
          false =>strs.push('('),
       }
   }).collect::<Vec<_>>()
   strs
}
```

二、精彩的解法

1、

```
fn duplicate_encode(word:&str)->String {
  let lower = String::from(word).to_lowercase();
  lower.chars().map(|c| if lower.find(c) == lower.rfind(c) { '(' } else { ')' }).collect()
}
```

2、

```
fn duplicate_encode(word:&str)->String {
  let mut res = String::from("")
  for (i,c) in word.to_lowercase().chars().enumerate() {
    res.push(if word.to_lowercase().chars().filter(|&x| x==c).count() > 1 { ')' } else { '(' })
  }
  res
}
```

3、

```
use std::collections::HashMap;

fn duplicate_encode(word: &str) -> String {
    let word = word.to_uppercase();
    let mut char_map = HashMap::new();
    for ch in word.chars() {
        let count = char_map.entry(ch).or_insert(0);
        *count += 1;
    }
    word.chars()
        .map(|ch| if *char_map.get(&ch).unwrap()  > 1 { ')' } else { '(' })
        .collect()
}
```

4、