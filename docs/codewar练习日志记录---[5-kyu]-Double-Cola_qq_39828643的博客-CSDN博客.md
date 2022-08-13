<!--yml
category: codewars
date: 2022-08-13 11:45:25
-->

# codewar练习日志记录---[5 kyu] Double Cola_qq_39828643的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_39828643/article/details/103686613?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-103686613.nonecase](https://blog.csdn.net/qq_39828643/article/details/103686613?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-103686613.nonecase)

### CodeWars [5 kyu] Double Cola[R]

## ***题目：***

Sheldon, Leonard, Penny, Rajesh and Howard are in the queue for a “Double Cola” drink vending machine; there are no other people in the queue. The first one in the queue (Sheldon) buys a can, drinks it and doubles! The resulting two Sheldons go to the end of the queue. Then the next in the queue (Leonard) buys a can, drinks it and gets to the end of the queue as two Leonards, and so on.

For example, Penny drinks the third can of cola and the queue will look like this:

Rajesh, Howard, Sheldon, Sheldon, Leonard, Leonard, Penny, Penny
Write a program that will return the name of the person who will drink the n-th cola.

Input
The input data consist of an array which contains at least 1 name, and single integer n which may go as high as the biggest number your language of choice supports (if there’s such limit, of course).

Output / Examples
Return the single line — the name of the person who drinks the n-th can of cola. The cans are numbered starting from 1.

```
who_is_next(c("Sheldon", "Leonard", "Penny", "Rajesh", "Howard"), 1) == "Sheldon"
who_is_next(c("Sheldon", "Leonard", "Penny", "Rajesh", "Howard"), 52) == "Penny"
who_is_next(c("Sheldon", "Leonard", "Penny", "Rajesh", "Howard"), 10010) == "Howard" 
```

## ***自己的答案：***

```
who_is_next <- function(names, r) {
    namesNumber<-rep(1,each=length(names))  
    count<-length(names);    
    while (r>count){
      r=r-count;
      count=count*2;
      namesNumber=namesNumber*2;
    }  
      i<-1;
      while (r>namesNumber[i]) {
        r=r-namesNumber[i];
        i=i+1;
      }  
      result<-names[i];
      return(result);  
} 
```

* * *

## 最佳答案：

* * *

```
who_is_next <- function(names, r) {
  l = length(names)
  while (r >= l) {
    r <- r-l
    l <- l*2
  }
  names[ceiling(length(names)*r/l)]
} 
```