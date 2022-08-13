<!--yml
category: codewars
date: 2022-08-13 11:46:05
-->

# Codewars - One Line Task 系列_wynist的博客-CSDN博客

> 来源：[https://blog.csdn.net/u012345506/article/details/119421015?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-119421015.nonecase](https://blog.csdn.net/u012345506/article/details/119421015?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-119421015.nonecase)

CG系列，把做了的贴一下。这网站快死了属于是😅

## One Line Task: Two Letters

```
toASCIINumber=(a,b)=>a[c='charCodeAt']()+''+b[c]()|0 
```

## One Line Task: Digits Average

```
digitsAverage=f=n=>n<10?n:f(+[...n+=''].map((a,i)=>a- -n[i-1]+1>>1).join('')) 
```

## One Line Task: Zero Or One

```
zeroOrOne=(n,s)=>s[0].map((_,i)=>s.map(a=>a[i]).sort()[n/2|0]) 
```

## One Line Task: Remove Zeros

```
removeZeros=a=>eval('['+/[1-9].*[1-9]/.exec(a)+']') 
```

## One Line Task: Strange Compare

```
strangeCompare=(a,k)=>a.sort(s=(a,b)=>a%10-b%10||s(a/10|0,b/10|0))[k] 
```

## One Line Task: Palindrome String

```
palindrome=p=(n,[c,...d])=>d!=false?c+p(n-2,d)+c:c.repeat(n) 
```

## One Line Task: Circle Intersection

```
with(Math)circleIntersection=([a,b],[c,d],r)=>(-sin(q=acos(hypot(c-a,d-b)/r/2)*2)+q)*r*r|0 
```

## One Line Task: Date Of Solar Calendar

```
solarDate=n=>(i=30,--n<186?i=31:n-=6,n-=(z=n%i),z+1+", "+"FOKTMSMAADBE"[f=n/i]+"arhiohebzeas"[f]) 
```

## One Line Task: Check Range

```
checkRange=(a,x,y)=>a.map(v=>d+=x>v==v>y,d=0)|d 
```