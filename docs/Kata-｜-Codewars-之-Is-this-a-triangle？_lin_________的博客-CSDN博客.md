<!--yml
category: codewars
date: 2022-08-13 11:50:06
-->

# Kata | Codewars 之 Is this a triangle?_lin_________的博客-CSDN博客

> 来源：[https://blog.csdn.net/lin_________/article/details/119951705?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-119951705.nonecase](https://blog.csdn.net/lin_________/article/details/119951705?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-119951705.nonecase)

> 题目：
> 
> Implement a method that accepts 3 integer values a, b, c. The method should return true if a triangle can be built with the sides of given length and false in any other case.
> 
> (In this case, all triangles must have surface greater than 0 to be accepted).

我写的：

```
namespace Triangle
{
  bool isTriangle(int a, int b, int c){
  long long la=a,lb=b,lc=c;
  if(la<=0||lb<=0||lc<=0){
      return false;}
  else {
		return a>0 and b>0 and c>0 and la-lb<lc and la-lc<lb and lb-lc<la and la+lb>lc and la+lc>lb and lb+lc>la;  
    }  
  }

}; 
```

 高手：

```
namespace Triangle
{
  bool isTriangle(int a, int b, int c)
  {
    return a-b<c && b-c<a && c-a<b;
  }
};
```