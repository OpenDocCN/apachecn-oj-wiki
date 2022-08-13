<!--yml
category: codewars
date: 2022-08-13 11:39:55
-->

# R语言Codewars实战——Rainfall_三只佩奇不结义的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41196612/article/details/108006192?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-108006192.142^v40^control,185^v2^control](https://blog.csdn.net/qq_41196612/article/details/108006192?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-108006192.142^v40^control,185^v2^control)

说明：这道题是真难到我了，主要是我不清楚怎么把字母之间的数字匹配出来，我初始的时候想的是正则表达式，但是R语言的正则表达式与我在python中学到的不同，且更加麻烦复杂，再者我又对正则表达式一知半解的，脑子真就慢慢变得迷糊了，直接看了别人的解法(整半天经验没变化，难受啊)。

# Description:

`data` and `data1` are two strings with rainfall records of a few cities for months from January to December. The records of towns are separated by `\n`. The name of each town is followed by `:`.

`data` and `towns` can be seen in “Your Test Cases:”.

# Task:

*   function: `mean(town, strng)` should return the average of rainfall for the city `town` and the `strng` `data` or `data1` (In R and Julia this function is called avg).

*   function: `variance(town, strng)` should return the variance of rainfall for the city `town` and the `strng` `data` or `data1`.

# Examples:

```
mean("London", data), 51.19(9999999999996) 
variance("London", data), 57.42(833333333374) 
```

# Notes:

*   if functions `mean` or `variance` have as parameter `town` a city which has no records return `-1` or `-1.0` (depending on the language)
*   Don’t truncate or round: the tests will pass if `abs(your_result - test_result) <= 1e-2` or `abs((your_result - test_result) / test_result) <= 1e-6` depending on the language.
*   Shell tests only variance
*   A ref: `http://www.mathsisfun.com/data/standard-deviation.html`
*   `data` and `data1` (can be named `d0` and `d1` depending on the language; see “Sample Tests:”) are adapted from: `http://www.worldclimate.com`

# Test Cases:

```
data0 <-
    "Rome:Jan 81.2,Feb 63.2,Mar 70.3,Apr 55.7,May 53.0,Jun 36.4,Jul 17.5,Aug 27.5,Sep 60.9,Oct 117.7,Nov 111.0,Dec 97.9
    London:Jan 48.0,Feb 38.9,Mar 39.9,Apr 42.2,May 47.3,Jun 52.1,Jul 59.5,Aug 57.2,Sep 55.4,Oct 62.0,Nov 59.0,Dec 52.9
    Paris:Jan 182.3,Feb 120.6,Mar 158.1,Apr 204.9,May 323.1,Jun 300.5,Jul 236.8,Aug 192.9,Sep 66.3,Oct 63.3,Nov 83.2,Dec 154.7
    NY:Jan 108.7,Feb 101.8,Mar 131.9,Apr 93.5,May 98.8,Jun 93.6,Jul 102.2,Aug 131.8,Sep 92.0,Oct 82.3,Nov 107.8,Dec 94.2
    Vancouver:Jan 145.7,Feb 121.4,Mar 102.3,Apr 69.2,May 55.8,Jun 47.1,Jul 31.3,Aug 37.0,Sep 59.6,Oct 116.3,Nov 154.6,Dec 171.5
    Sydney:Jan 103.4,Feb 111.0,Mar 131.3,Apr 129.7,May 123.0,Jun 129.2,Jul 102.8,Aug 80.3,Sep 69.3,Oct 82.6,Nov 81.4,Dec 78.2
    Bangkok:Jan 10.6,Feb 28.2,Mar 30.7,Apr 71.8,May 189.4,Jun 151.7,Jul 158.2,Aug 187.0,Sep 319.9,Oct 230.8,Nov 57.3,Dec 9.4
    Tokyo:Jan 49.9,Feb 71.5,Mar 106.4,Apr 129.2,May 144.0,Jun 176.0,Jul 135.6,Aug 148.5,Sep 216.4,Oct 194.1,Nov 95.6,Dec 54.4
    Beijing:Jan 3.9,Feb 4.7,Mar 8.2,Apr 18.4,May 33.0,Jun 78.1,Jul 224.3,Aug 170.0,Sep 58.4,Oct 18.0,Nov 9.3,Dec 2.7
    Lima:Jan 1.2,Feb 0.9,Mar 0.7,Apr 0.4,May 0.6,Jun 1.8,Jul 4.4,Aug 3.1,Sep 3.3,Oct 1.7,Nov 0.5,Dec 0.7";

data1 <-
    "Rome:Jan 90.2,Feb 73.2,Mar 80.3,Apr 55.7,May 53.0,Jun 36.4,Jul 17.5,Aug 27.5,Sep 60.9,Oct 147.7,Nov 121.0,Dec 97.9
    London:Jan 58.0,Feb 38.9,Mar 49.9,Apr 42.2,May 67.3,Jun 52.1,Jul 59.5,Aug 77.2,Sep 55.4,Oct 62.0,Nov 69.0,Dec 52.9
    Paris:Jan 182.3,Feb 120.6,Mar 188.1,Apr 204.9,May 323.1,Jun 350.5,Jul 336.8,Aug 192.9,Sep 66.3,Oct 63.3,Nov 83.2,Dec 154.7
    NY:Jan 128.7,Feb 121.8,Mar 151.9,Apr 93.5,May 98.8,Jun 93.6,Jul 142.2,Aug 131.8,Sep 92.0,Oct 82.3,Nov 107.8,Dec 94.2
    Vancouver:Jan 155.7,Feb 121.4,Mar 132.3,Apr 69.2,May 85.8,Jun 47.1,Jul 31.3,Aug 37.0,Sep 69.6,Oct 116.3,Nov 154.6,Dec 171.5
    Sydney:Jan 123.4,Feb 111.0,Mar 151.3,Apr 129.7,May 123.0,Jun 159.2,Jul 102.8,Aug 90.3,Sep 69.3,Oct 82.6,Nov 81.4,Dec 78.2
    Bangkok:Jan 20.6,Feb 28.2,Mar 40.7,Apr 81.8,May 189.4,Jun 151.7,Jul 198.2,Aug 197.0,Sep 319.9,Oct 230.8,Nov 57.3,Dec 9.4
    Tokyo:Jan 59.9,Feb 81.5,Mar 106.4,Apr 139.2,May 144.0,Jun 186.0,Jul 155.6,Aug 148.5,Sep 216.4,Oct 194.1,Nov 95.6,Dec 54.4
    Beijing:Jan 13.9,Feb 14.7,Mar 18.2,Apr 18.4,May 43.0,Jun 88.1,Jul 224.3,Aug 170.0,Sep 58.4,Oct 38.0,Nov 19.3,Dec 2.7
    Lima:Jan 11.2,Feb 10.9,Mar 10.7,Apr 10.4,May 10.6,Jun 11.8,Jul 14.4,Aug 13.1,Sep 23.3,Oct 1.7,Nov 0.5,Dec 10.7";

towns <- c("Rome", "London", "Lond", "Paris", "NY", "Vancouver", "Sydney", "Bangkok", "Tokyo",
               "Beijing", "Beiging", "Lima", "Montevideo", "Caracas", "Madrid", "Berlin", "Lon");

testingMean <- function(town, strng, expected) {
    actual <- avg(town, strng)

    expect_equal(actual, expected, tol = 1e-6, scale =  1, info = "")
}
testingVariance <- function(town, strng, expected) {
    actual <- variance(town, strng)

    expect_equal(actual, expected, tol = 1e-6, scale =  1, info = "")
}

test_that("tests avg data0", {
    testingMean("London", data0, 51.199999999999996) 
    testingMean("Beijing", data0, 52.416666666666664)
})
test_that("tests avg data1", {
    testingMean("London", data1, 57.03333333333333) 
    testingMean("Beijing", data1, 59.083333333333336)
})
test_that("tests variance data0", {
    testingVariance("London", data0, 57.42833333333374) 
    testingVariance("Beijing", data0, 4808.37138888889)
})
test_that("tests variance data1", {
    testingVariance("London", data1, 110.90055555555546) 
    testingVariance("Beijing", data1, 4437.038055555556)
})

meanvarAux1333 <- function(town, strng) {
    rg <- regexpr(paste0(town, ":.*?(?:\n|$)"), strng, perl=TRUE);
    twn <- regmatches(strng, rg);
    if (length(twn) == 0) return(c(-1, -1));
    stat <- as.numeric(unlist(regmatches(twn, gregexpr("[[:digit:]]+\\.*[[:digit:]]*", twn))));
    c(mean(stat), var(stat)*11/12);
}
avg1333 <- function(town, strng) {
    meanvarAux1333(town, strng)[1]
}
variance1333 <- function(town, strng) {
    meanvarAux1333(town, strng)[2]
}
yTests <- function() {
    twns <- sample(towns)
    for (t in twns) {

        testingMean(t, data0, avg1333(t, data0))
    }
}
test_that("Random tests avg with data0", {
    yTests()
})
zTests <- function() {
    twns <- sample(towns)
    for (t in twns) {

        testingVariance(t, data1, variance1333(t, data1))
    }
}
test_that("Random tests variance with data1", {
    zTests()
}) 
```

# 实现

## 代码1：

```
avg <- function(town, strng) {
  d0 <- trimws(unlist(strsplit(strng, ":|\n")))
  cities <- d0[c(TRUE, FALSE)]
  vals <- as.numeric(gsub("[^0-9.]", "", unlist(strsplit(d0[2 * match(town, cities)], ","))))
  ifelse(anyNA(vals), -1, mean(vals))
}
variance <- function(town, strng) {
  d0 <- trimws(unlist(strsplit(strng, ":|\n")))
  cities <- d0[c(TRUE, FALSE)]
  vals <- as.numeric(gsub("[^0-9.]", "", unlist(strsplit(d0[2 * match(town, cities)], ","))))
  ifelse(anyNA(vals), -1, sum((vals - mean(vals))^2) / length(vals))
} 
```

我学到的东西：

*   第一，`strsplit`函数中的`split`参数可以同时设置几个不同的分割符，但不同的分割符之间需要用`"|"`分开，这是让我非常意外的一个点，早知道还可以这样，我就直接这么强行解出这道题了，还整那么复杂的正则表达式干啥啊。我对这位作者的代码进行了些微的改动，添加了空格，因此`split`参数将改为`":|\n| "`，最后是一个空格，可能不太明显，凑合着看吧（Tips：不建议添加空格，因为`trimws`函数可以去除头部或者尾部的空格，下面作为第二点详细地讲讲吧）。

*   第二，第一次见`trimws`函数，仔细看了看帮助文档，文档说明是这样的：`"Remove leading and/or trailing whitespace from character strings."`，光说不做假把式，直接给几个具体的例子好理解一些。可以看到，使用函数之后，每一个字符串首部和尾部的的空格都没了。

```
 > unlist(strsplit(strng, ":|\n"))
 [1] "Rome"                                                                                                                
 [2] "Jan 81.2,Feb 63.2,Mar 70.3,Apr 55.7,May 53.0,Jun 36.4,Jul 17.5,Aug 27.5,Sep 60.9,Oct 117.7,Nov 111.0,Dec 97.9"       
 [3] "    London"                                                                                                          
 [4] "Jan 48.0,Feb 38.9,Mar 39.9,Apr 42.2,May 47.3,Jun 52.1,Jul 59.5,Aug 57.2,Sep 55.4,Oct 62.0,Nov 59.0,Dec 52.9"         
 [5] "    Paris"                                                                                                           
 [6] "Jan 182.3,Feb 120.6,Mar 158.1,Apr 204.9,May 323.1,Jun 300.5,Jul 236.8,Aug 192.9,Sep 66.3,Oct 63.3,Nov 83.2,Dec 154.7"
 [7] "    NY"                                                                                                              
 [8] "Jan 108.7,Feb 101.8,Mar 131.9,Apr 93.5,May 98.8,Jun 93.6,Jul 102.2,Aug 131.8,Sep 92.0,Oct 82.3,Nov 107.8,Dec 94.2"   
 [9] "    Vancouver"                                                                                                       
[10] "Jan 145.7,Feb 121.4,Mar 102.3,Apr 69.2,May 55.8,Jun 47.1,Jul 31.3,Aug 37.0,Sep 59.6,Oct 116.3,Nov 154.6,Dec 171.5"   
[11] "    Sydney"                                                                                                          
[12] "Jan 103.4,Feb 111.0,Mar 131.3,Apr 129.7,May 123.0,Jun 129.2,Jul 102.8,Aug 80.3,Sep 69.3,Oct 82.6,Nov 81.4,Dec 78.2"  
[13] "    Bangkok"                                                                                                         
[14] "Jan 10.6,Feb 28.2,Mar 30.7,Apr 71.8,May 189.4,Jun 151.7,Jul 158.2,Aug 187.0,Sep 319.9,Oct 230.8,Nov 57.3,Dec 9.4"    
[15] "    Tokyo"                                                                                                           
[16] "Jan 49.9,Feb 71.5,Mar 106.4,Apr 129.2,May 144.0,Jun 176.0,Jul 135.6,Aug 148.5,Sep 216.4,Oct 194.1,Nov 95.6,Dec 54.4" 
[17] "    Beijing"                                                                                                         
[18] "Jan 3.9,Feb 4.7,Mar 8.2,Apr 18.4,May 33.0,Jun 78.1,Jul 224.3,Aug 170.0,Sep 58.4,Oct 18.0,Nov 9.3,Dec 2.7"            
[19] "    Lima"                                                                                                            
[20] "Jan 1.2,Feb 0.9,Mar 0.7,Apr 0.4,May 0.6,Jun 1.8,Jul 4.4,Aug 3.1,Sep 3.3,Oct 1.7,Nov 0.5,Dec 0.7"  

> trimws(unlist(strsplit(strng, ":|\n")))
 [1] "Rome"                                                                                                                
 [2] "Jan 81.2,Feb 63.2,Mar 70.3,Apr 55.7,May 53.0,Jun 36.4,Jul 17.5,Aug 27.5,Sep 60.9,Oct 117.7,Nov 111.0,Dec 97.9"       
 [3] "London"                                                                                                              
 [4] "Jan 48.0,Feb 38.9,Mar 39.9,Apr 42.2,May 47.3,Jun 52.1,Jul 59.5,Aug 57.2,Sep 55.4,Oct 62.0,Nov 59.0,Dec 52.9"         
 [5] "Paris"                                                                                                               
 [6] "Jan 182.3,Feb 120.6,Mar 158.1,Apr 204.9,May 323.1,Jun 300.5,Jul 236.8,Aug 192.9,Sep 66.3,Oct 63.3,Nov 83.2,Dec 154.7"
 [7] "NY"                                                                                                                  
 [8] "Jan 108.7,Feb 101.8,Mar 131.9,Apr 93.5,May 98.8,Jun 93.6,Jul 102.2,Aug 131.8,Sep 92.0,Oct 82.3,Nov 107.8,Dec 94.2"   
 [9] "Vancouver"                                                                                                           
[10] "Jan 145.7,Feb 121.4,Mar 102.3,Apr 69.2,May 55.8,Jun 47.1,Jul 31.3,Aug 37.0,Sep 59.6,Oct 116.3,Nov 154.6,Dec 171.5"   
[11] "Sydney"                                                                                                              
[12] "Jan 103.4,Feb 111.0,Mar 131.3,Apr 129.7,May 123.0,Jun 129.2,Jul 102.8,Aug 80.3,Sep 69.3,Oct 82.6,Nov 81.4,Dec 78.2"  
[13] "Bangkok"                                                                                                             
[14] "Jan 10.6,Feb 28.2,Mar 30.7,Apr 71.8,May 189.4,Jun 151.7,Jul 158.2,Aug 187.0,Sep 319.9,Oct 230.8,Nov 57.3,Dec 9.4"    
[15] "Tokyo"                                                                                                               
[16] "Jan 49.9,Feb 71.5,Mar 106.4,Apr 129.2,May 144.0,Jun 176.0,Jul 135.6,Aug 148.5,Sep 216.4,Oct 194.1,Nov 95.6,Dec 54.4" 
[17] "Beijing"                                                                                                             
[18] "Jan 3.9,Feb 4.7,Mar 8.2,Apr 18.4,May 33.0,Jun 78.1,Jul 224.3,Aug 170.0,Sep 58.4,Oct 18.0,Nov 9.3,Dec 2.7"            
[19] "Lima"                                                                                                                
[20] "Jan 1.2,Feb 0.9,Mar 0.7,Apr 0.4,May 0.6,Jun 1.8,Jul 4.4,Aug 3.1,Sep 3.3,Oct 1.7,Nov 0.5,Dec 0.7" 
```

*   第三，使用`TRUE,FALSE`作为列表的索引，百度老半天也没个结果，然后我就尝试了几个例子，总算是弄明白了，接下来展示代码与结果。可以看到，索引为`c(TRUE,FALSE)`时，其实相当于`d0[c(取, 不取, 取, 不取...)]`，也就是`TRUE`对应的位置取，`FALSE`的不取，如此循环遍历整个列表。为了验证我的结论，我又添加了一项，把索引改为了`c(TRUE,FALSE,TRUE)`，结果很显然，结果为`d0[c(取, 不取, 取, 取, 不取, 取,...)]`，`TRUE`对应的仍然是取，否则不取，与前面的结论一致。

```
> d0
 [1] "Rome"                                                                                                                
 [2] "Jan 81.2,Feb 63.2,Mar 70.3,Apr 55.7,May 53.0,Jun 36.4,Jul 17.5,Aug 27.5,Sep 60.9,Oct 117.7,Nov 111.0,Dec 97.9"       
 [3] "London"                                                                                                              
 [4] "Jan 48.0,Feb 38.9,Mar 39.9,Apr 42.2,May 47.3,Jun 52.1,Jul 59.5,Aug 57.2,Sep 55.4,Oct 62.0,Nov 59.0,Dec 52.9"         
 [5] "Paris"                                                                                                               
 [6] "Jan 182.3,Feb 120.6,Mar 158.1,Apr 204.9,May 323.1,Jun 300.5,Jul 236.8,Aug 192.9,Sep 66.3,Oct 63.3,Nov 83.2,Dec 154.7"
 [7] "NY"                                                                                                                  
 [8] "Jan 108.7,Feb 101.8,Mar 131.9,Apr 93.5,May 98.8,Jun 93.6,Jul 102.2,Aug 131.8,Sep 92.0,Oct 82.3,Nov 107.8,Dec 94.2"   
 [9] "Vancouver"                                                                                                           
[10] "Jan 145.7,Feb 121.4,Mar 102.3,Apr 69.2,May 55.8,Jun 47.1,Jul 31.3,Aug 37.0,Sep 59.6,Oct 116.3,Nov 154.6,Dec 171.5"   
[11] "Sydney"                                                                                                              
[12] "Jan 103.4,Feb 111.0,Mar 131.3,Apr 129.7,May 123.0,Jun 129.2,Jul 102.8,Aug 80.3,Sep 69.3,Oct 82.6,Nov 81.4,Dec 78.2"  
[13] "Bangkok"                                                                                                             
[14] "Jan 10.6,Feb 28.2,Mar 30.7,Apr 71.8,May 189.4,Jun 151.7,Jul 158.2,Aug 187.0,Sep 319.9,Oct 230.8,Nov 57.3,Dec 9.4"    
[15] "Tokyo"                                                                                                               
[16] "Jan 49.9,Feb 71.5,Mar 106.4,Apr 129.2,May 144.0,Jun 176.0,Jul 135.6,Aug 148.5,Sep 216.4,Oct 194.1,Nov 95.6,Dec 54.4" 
[17] "Beijing"                                                                                                             
[18] "Jan 3.9,Feb 4.7,Mar 8.2,Apr 18.4,May 33.0,Jun 78.1,Jul 224.3,Aug 170.0,Sep 58.4,Oct 18.0,Nov 9.3,Dec 2.7"            
[19] "Lima"                                                                                                                
[20] "Jan 1.2,Feb 0.9,Mar 0.7,Apr 0.4,May 0.6,Jun 1.8,Jul 4.4,Aug 3.1,Sep 3.3,Oct 1.7,Nov 0.5,Dec 0.7" 

> d0[c(TRUE, FALSE)]
 [1] "Rome"      "London"    "Paris"     "NY"        "Vancouver" "Sydney"    "Bangkok"   "Tokyo"     "Beijing"   "Lima" 

> d0[c(TRUE,FALSE,TRUE)]
 [1] "Rome"                                                                                                                
 [2] "London"                                                                                                              
 [3] "Jan 48.0,Feb 38.9,Mar 39.9,Apr 42.2,May 47.3,Jun 52.1,Jul 59.5,Aug 57.2,Sep 55.4,Oct 62.0,Nov 59.0,Dec 52.9"         
 [4] "Jan 182.3,Feb 120.6,Mar 158.1,Apr 204.9,May 323.1,Jun 300.5,Jul 236.8,Aug 192.9,Sep 66.3,Oct 63.3,Nov 83.2,Dec 154.7"
 [5] "NY"                                                                                                                  
 [6] "Vancouver"                                                                                                           
 [7] "Jan 145.7,Feb 121.4,Mar 102.3,Apr 69.2,May 55.8,Jun 47.1,Jul 31.3,Aug 37.0,Sep 59.6,Oct 116.3,Nov 154.6,Dec 171.5"   
 [8] "Jan 103.4,Feb 111.0,Mar 131.3,Apr 129.7,May 123.0,Jun 129.2,Jul 102.8,Aug 80.3,Sep 69.3,Oct 82.6,Nov 81.4,Dec 78.2"  
 [9] "Bangkok"                                                                                                             
[10] "Tokyo"                                                                                                               
[11] "Jan 49.9,Feb 71.5,Mar 106.4,Apr 129.2,May 144.0,Jun 176.0,Jul 135.6,Aug 148.5,Sep 216.4,Oct 194.1,Nov 95.6,Dec 54.4" 
[12] "Jan 3.9,Feb 4.7,Mar 8.2,Apr 18.4,May 33.0,Jun 78.1,Jul 224.3,Aug 170.0,Sep 58.4,Oct 18.0,Nov 9.3,Dec 2.7"            
[13] "Lima" 
```

*   第四，`anyNA`函数与`any`函数的思想是一样的，只要有一个是`TRUE`该函数的返回值就会是`TRUE`，因此在这里就不再多讲了。主要还是讲讲`ifelse`函数，该函数比使用`if-else`要好多了，主要还是因为`ifelse`还可以直接分别判别一个向量，并返回与向量同长度的结果，换句话说，就是`ifelse`函数可以做批处理，大大地提高程序的运行效率。

## 代码2

```
readings <- function(town, strng) {
  lines <- strsplit(strng, "\n")[[1]]
  idx <- which(grepl(paste0("^ *", town, ":"), lines))
  if (length(idx) == 0) {
    return(NULL)
  }
  as.numeric(strsplit(gsub("[^0-9.,]", "", lines[idx]), ",")[[1]])
}
avg <- function(town, strng) {
  r <- readings(town, strng)
  if (is.null(r)) -1 else mean(r)
}
variance <- function(town, strng) {
  r <- readings(town, strng)
  if (is.null(r)) -1 else var(r) * 11 / 12
} 
```

**我在这个代码上学到的知识：**

*   第一，`grepl`的具体使用方法见我发的Codewars的第一篇文章[文章链接](https://blog.csdn.net/qq_41196612/article/details/107972568)，在这里就不再讲了。主要还是讲讲用到的正则表达式：`^ * town:`，我试了一下，可以把`*`去掉，`^town`的意思是匹配以`town`为首的字符串。接着是正则表达式`[^0-9.,]`意思是找出非0-9的数字、非`.`和非`,`。
*   第二，emmmm，好像没了，那就这么多了，以后要是再有什么新想法再说吧。