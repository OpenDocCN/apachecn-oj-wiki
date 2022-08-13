<!--yml
category: codewars
date: 2022-08-13 11:39:36
-->

# codewars——codewars——Bit Counting_熊熊玩python的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41552148/article/details/99234433?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-99234433-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_41552148/article/details/99234433?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-99234433-null-null.142^v40^control,185^v2^control&utm_term=codewars)

> Write a function that takes an integer as input, and returns the number of bits that are equal to one in the binary representation of that number. You can guarantee that input is non-negative.Example: The binary representation of 1234 is 10011010010, so the function should return 5 in this case

# 思路

啧啧，如果是python代码这道题毫无难度，如果用C++的话，我确实也不知道C++有哪些轮子，估计得自己造轮子了。

## 十进制转二进制

原理就是一直对余数取对2的模，直到商为0，然后把余数倒序即可。我自己造轮子吧，希望时间上不会太久。

```
#include <vector>
#include <iostream>
using namespace std;
unsigned int countBits(unsigned long long n);
int main()
{
    cout << countBits(0) << endl;
    return 0;
}
unsigned int countBits(unsigned long long n)
{
    if (n == 0)
        return 0;
    unsigned int count = 0;
    cout << "start n:" << n << endl;
    vector<unsigned int> T;
    do
    {
        T.push_back(n % 2);
        n /= 2;
    } while (n / 2 != 0);
    T.push_back(1);
    for (auto p = T.begin(); p != T.end(); ++p)
    {
        if (*p == 1)
        {
            count++;
        }
    }
    return count;
} 
```

代码来咯，首个用C++写的codewars，对我来说是个里程碑。
但是……不得不说python真的简单，来看一下python代码

```
def count(n):
    return str(bin(n)).count('1') 
```