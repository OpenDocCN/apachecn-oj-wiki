<!--yml
category: codewars
date: 2022-08-13 11:51:21
-->

# [Codewars]A Rule of Divisibility by 13-6kyu_paramecia.的博客-CSDN博客

> 来源：[https://blog.csdn.net/Maaa_25/article/details/105399792?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-105399792.nonecase](https://blog.csdn.net/Maaa_25/article/details/105399792?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-105399792.nonecase)

### 题目说明

```
When you divide the successive powers of 10 by 13 you get the following remainders of the integer divisions:

1, 10, 9, 12, 3, 4.

Then the whole pattern repeats.

Hence the following method: Multiply the right most digit of the number with the left most number in the sequence shown above, the second right most digit to the second left most digit of the number in the sequence. The cycle goes on and you sum all these products. Repeat this process until the sequence of sums is stationary.

...........................................................................

Example: What is the remainder when 1234567 is divided by 13?

7×1 + 6×10 + 5×9 + 4×12 + 3×3 + 2×4 + 1×1 = 178

We repeat the process with 178:

8x1 + 7x10 + 1x9 = 87

and again with 87:

7x1 + 8x10 = 87

...........................................................................

From now on the sequence is stationary and the remainder of 1234567 by 13 is the same as the remainder of 87 by 13: 9

Call thirt the function which processes this sequence of operations on an integer n (>=0). thirt will return the stationary number.

thirt(1234567) calculates 178, then 87, then 87 and returns 87.

thirt(321) calculates 48, 48 and returns 48 
```

### 我的想法

emmm其实很惭愧，这次是解锁了solution以后再回过头来做的。
题目要求我们对一个数逐位做相应数乘运算后求和，若和与被运算的数相同，则输出。
一开始的想法是使用string类和sstream来做，将数字转换为string类后,逐位按照要求相乘后输出。但可能是我代码的问题，最后显示time out。
那我们就换种思路，从数学的角度看看。我用`sum`表示当前求到的和，`before`表示前一次求到的和，用一个数组`factor[]`存储题目所给的条件乘数。
第一个关键点是如何取出各位数。可以对数n用求余运算符`%`取出当前位数，将数n除以10后进行下一轮循环。终止条件是n>0（没得再除下去了）。第二个关键点是条件的刷新，这里我一开始不小心也被绕进去了。当计算完当前数以后，需要将这个“当前数”赋给“之前数”，然后把“当前数”重置为0，开始新一轮计算。当`sum==before`时停止。

### 我的代码实现

```
class Thirteen
{
public:
    static long long thirt(long long n);
};
long long Thirteen::thirt(long long n)
{
    long long sum=n,before=0;
    int factor[] = {1,10,9,12,3,4};
    while(sum != before)
    {
        before = sum;
        sum =0;
        int i=0;
        n = before;
        while( n>0 )
        {
            sum += (n%10) * factor[i%6];
            i++;
            n  = n/10;
        }
    }
    return sum;
} 
```

### 大神代码实现

```
 class Thirteen
{
public:
static long long thirt(long long n)
{
   std::vector <int> coeffs = {1,10,9,12,3,4};
   std::string number = std::to_string(n);
   long long sum = 0;
   for( int i= number.size()-1; i >=0 ; --i)
   {
      sum+= coeffs[(number.size()-1-i)%coeffs.size()]*(number[i]-'0');
   }
   if(n==sum) return n;
   else return thirt(sum);
}
}; 
```

```
class Thirteen
{
public:
    static long long thirt(long long n);
};

long long Thirteen::thirt(long long n){
  int divs[6] = {1, 10, 9, 12, 3, 4};
  while(n >= 100){
    long long aux = n;
    n = 0;

    for(int i = 0; aux != 0; n += (aux%10)*divs[i%6], aux /= 10, i++);
  }
  return n;

} 
```