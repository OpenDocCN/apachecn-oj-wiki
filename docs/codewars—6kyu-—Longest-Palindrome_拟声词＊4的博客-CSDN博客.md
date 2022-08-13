<!--yml
category: codewars
date: 2022-08-13 11:42:29
-->

# codewars—6kyu —Longest Palindrome_拟声词*4的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_53054309/article/details/115027167?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-15-115027167-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_53054309/article/details/115027167?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-15-115027167-null-null.142^v40^control,185^v2^control&utm_term=codewars)

Find the length of the longest substring in the given string s that is the same in reverse.

As an example, if the input was “I like racecars that go fast”, the substring (racecar) length would be 7.

If the length of the input string is 0, the return value must be 0.

```
#include <string.h>
#include <stdio.h>

int longest_palindrome(const char *s)
{

  int i,j=0,max=0,len=(int)strlen(s),cnt=0,t,p;
  printf("string=%s\n",s);
  if(len==1)
    return 1;
  //特殊情况判断

  for(i=0;i<len;i++)
  {
     for(j=len-1;j>i;j--)
    {
      //两层循环
      if(s[i]==s[j] && j-i>max)
        {
        cnt=0;
        printf("i=%d j=%d\n",i,j);
           t=i,p=j;
           while(p-t>=1 )
            {
              if(s[t++]==s[p--])
                cnt+=2;
               else 
               {
                 cnt=1;
                 break;
               }

             }
         if((j-i+1)%2!=0)
             cnt++;  
          printf("cnt=%d\n",cnt);
          }
        if(cnt>max)
          max=cnt;
       }

  }

printf("max =%d\n",max);
  printf("\n\n\n");
return max; //your code here
} 
```