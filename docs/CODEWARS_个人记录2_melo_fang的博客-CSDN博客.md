<!--yml
category: codewars
date: 2022-08-13 11:29:12
-->

# CODEWARS_个人记录2_melo_fang的博客-CSDN博客

> 来源：[https://blog.csdn.net/melo_fang/article/details/79978585?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-79978585.142^v40^control,185^v2^control](https://blog.csdn.net/melo_fang/article/details/79978585?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-79978585.142^v40^control,185^v2^control)

4 kyu

题目：Roman Numerals Encoder

DESCRIPTION:

```
Create a function taking a positive integer as its parameter and returning a string containing the Roman Numeral representation of that integer.

Modern Roman numerals are written by expressing each digit separately starting with the left most digit and skipping any digit with a value of zero. In Roman numerals 1990 is rendered: 1000=M, 900=CM, 90=XC; resulting in MCMXC. 2008 is written as 2000=MM, 8=VIII; or MMVIII. 1666 uses each Roman symbol in descending order: MDCLXVI.

Example:

solution(1000); // => "M"
Help:

Symbol    Value
I          1
V          5
X          10
L          50
C          100
D          500
M          1,000
Remember that there can't be more than 3 identical symbols in a row.
```

My solution:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
char sym[7] = {'I','V','X','L','C','D','M'};

void myfun(int n,int flag,char *res){
    printf("n=%d\n",n);
    switch(n){
        case 1:
          sprintf(res,"%c",sym[flag*2]);
        break;
        case 2:
          sprintf(res,"%c%c",sym[flag*2],sym[flag*2]);
        break;
        case 3:
          sprintf(res,"%c%c%c",sym[flag*2],sym[flag*2],sym[flag*2]);
        break;
        case 4:
          sprintf(res,"%c%c",sym[flag*2],sym[flag*2+1]);
        break;
        case 5:
          sprintf(res,"%c",sym[flag*2+1]);
        break;
        case 6:
          sprintf(res,"%c%c",sym[flag*2+1],sym[flag*2]);
        break;
        case 7:
          sprintf(res,"%c%c%c",sym[flag*2+1],sym[flag*2],sym[flag*2]);
        break;
        case 8:
          sprintf(res,"%c%c%c%c",sym[flag*2+1],sym[flag*2],sym[flag*2],sym[flag*2]);
        break;
        case 9:
          sprintf(res,"%c%c",sym[flag*2],sym[(flag+1)*2]);
        break;
    } 
}

char *solution(int n) {
  // Your code here
  int num;
  int i=0;
  int len=0;
  char temp[100];
  char *res = malloc(255);

  res[0]= '\0';
  while(n){
    num = n%10;
    if(num){
      myfun(num,i,temp);
      strcat(temp,res);
      sprintf(res,"%s",temp);
    }
    n /= 10;
    i++;
  }
  printf("%s\n",res);
  return res;
}
```