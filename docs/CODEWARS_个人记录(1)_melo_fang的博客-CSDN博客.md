<!--yml
category: codewars
date: 2022-08-13 11:43:29
-->

# CODEWARS_个人记录(1)_melo_fang的博客-CSDN博客

> 来源：[https://blog.csdn.net/melo_fang/article/details/79978454?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-79978454.nonecase](https://blog.csdn.net/melo_fang/article/details/79978454?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-79978454.nonecase)

4 kyu

题目:String MIX

描述：

```
Given two strings s1 and s2, we want to visualize how different the two strings are. We will only take into account the lowercase letters (a to z). First let us count the frequency of each lowercase letters in s1 and s2.

s1 = "A aaaa bb c"

s2 = "& aaa bbb c d"

s1 has 4 'a', 2 'b', 1 'c'

s2 has 3 'a', 3 'b', 1 'c', 1 'd'

So the maximum for 'a' in s1 and s2 is 4 from s1; the maximum for 'b' is 3 from s2\. In the following we will not consider letters when the maximum of their occurrences is less than or equal to 1.

We can resume the differences between s1 and s2 in the following string: "1:aaaa/2:bbb" where 1 in 1:aaaa stands for string s1 and aaaa because the maximum for a is 4\. In the same manner 2:bbb stands for string s2 and bbb because the maximum for b is 3.

The task is to produce a string in which each lowercase letters of s1 or s2 appears as many times as its maximum if this maximum is strictly greater than 1; these letters will be prefixed by the number of the string where they appear with their maximum value and :. If the maximum is in s1 as well as in s2 the prefix is =:.

In the result, substrings (a substring is for example 2:nnnnn or 1:hhh; it contains the prefix) will be in decreasing order of their length and when they have the same length sorted in ascending lexicographic order (letters and digits - more precisely sorted by codepoint); the different groups will be separated by '/'. See examples and "Example Tests".

Hopefully other examples can make this clearer.

s1 = "my&friend&Paul has heavy hats! &"
s2 = "my friend John has many many friends &"
mix(s1, s2) --> "2:nnnnn/1:aaaa/1:hhh/2:mmm/2:yyy/2:dd/2:ff/2:ii/2:rr/=:ee/=:ss"

s1 = "mmmmm m nnnnn y&friend&Paul has heavy hats! &"
s2 = "my frie n d Joh n has ma n y ma n y frie n ds n&"
mix(s1, s2) --> "1:mmmmmm/=:nnnnnn/1:aaaa/1:hhh/2:yyy/2:dd/2:ff/2:ii/2:rr/=:ee/=:ss"

s1="Are the kids at home? aaaaa fffff"
s2="Yes they are here! aaaaa fffff"
mix(s1, s2) --> "=:aaaaaa/2:eeeee/=:fffff/1:tt/2:rr/=:hh"
Note for Swift, R

The prefix =: is replaced by E:

s1 = "mmmmm m nnnnn y&friend&Paul has heavy hats! &"
s2 = "my frie n d Joh n has ma n y ma n y frie n ds n&"
mix(s1, s2) --> "1:mmmmmm/=:nnnnnn/1:aaaa/1:hhh/2:yyy/2:dd/2:ff/2:ii/2:rr/E:ee/E:ss"
```

我的答案：

```
typedef struct ff{
    int num1;
    int num2;
    char zimu;
}FF;

char* mix(char* s1, char* s2) {
  // your code
  int xb[26]; 
  int i,j,temp,m,n,num1,num2;
  int cc=0;
  FF *res;
  res = (FF *)malloc(sizeof(struct ff)*26);
  char *ptr = malloc(1024);

  for(i=0;i<26;i++)
  {
    res[i].zimu = 97+i;
    res[i].num1 = 0;
    res[i].num2 = 0;
    xb[i] = i;

  }

  for(i=0;i<strlen(s1);i++)
  {
    if(s1[i]>96 && s1[i]<123)
    {
        res[s1[i]-97].num1 += 1;
    }
  }

  for(i=0;i<strlen(s2);i++)
  {
    if(s2[i]>96 && s2[i]<123)
    {
      res[s2[i]-97].num2 += 1;
    }
  }

  for(i=0;i<26;i++)
  {

      for(j=0;j<25-i;j++)
      {
          m = res[xb[j]].num1 > res[xb[j]].num2 ? res[xb[j]].num1 : res[xb[j]].num2;
          n = res[xb[j+1]].num1 > res[xb[j+1]].num2 ? res[xb[j+1]].num1 : res[xb[j+1]].num2;

          if(m<n)
          {
              temp = xb[j];
              xb[j] = xb[j+1];
              xb[j+1] = temp;
          }
          else if(m==n)
          { 
               num1 = res[xb[j]].num1;
               num2 = res[xb[j]].num2;
               if(num1>num2)
                  m=0;
               else if(num1<num2)
                  m=1;
               else
                  m =2;

               num1 = res[xb[j+1]].num1;
               num2 = res[xb[j+1]].num2;
               if(num1>num2)
                  n=0;
               else if(num1<num2)
                  n=1;
               else
                  n =2;

               if(m>n)
                {
                 temp = xb[j];
                 xb[j] = xb[j+1];
                 xb[j+1] = temp;
                }
          }
      }
  }

  for(i=0;i<26;i++)
  {
      if(res[xb[i]].num1<2 && res[xb[i]].num2<2)
          break;
       m = res[xb[i]].num1;
       n = res[xb[i]].num2;
       if(m>n)
       {   ptr[cc] = '1';
           temp = m;}
       else if(m<n)
       {   ptr[cc] =  '2';temp = n;}
       else
       {   ptr[cc] = '=';temp = m;}

        cc++;
        ptr[cc++] = ':';
        for(j=0;j<temp;j++)
        {
            ptr[cc++] = res[xb[i]].zimu;
        }
        ptr[cc++] = '/';    
  }
   printf("s1:%s\n",s1);
  printf("s2:%s\n",s2);
  if(cc){
    ptr[cc-1] = '\0';
    printf("%s\n",ptr);
  }
  else
  {

      free(ptr);
      return "";
      //ptr = 0;

  }

  free(res);
  return ptr;
}
```

总结：这道题是在看了一天学堂在线之后刷的，用时1个小时，处理的时候很粗糙，就是暴力解决

    遇到的几个问题：1是数组的越界，在冒泡里交换下标数组时当时有问题，导致后面越界了

                            2是返回空指针的处理