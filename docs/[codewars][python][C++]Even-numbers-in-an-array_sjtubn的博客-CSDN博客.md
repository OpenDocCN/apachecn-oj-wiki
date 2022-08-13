<!--yml
category: codewars
date: 2022-08-13 11:51:08
-->

# [codewars][python][C++]Even numbers in an array_sjtubn的博客-CSDN博客

> 来源：[https://blog.csdn.net/sjtubn/article/details/87790044?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-87790044.nonecase](https://blog.csdn.net/sjtubn/article/details/87790044?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-87790044.nonecase)

Given an `array` of digitals numbers, return a new array of length `number` containing the last even numbers from the original array (in the same order). The original array will be not empty and will contain at least "number" even numbers.

For example:

```
([1, 2, 3, 4, 5, 6, 7, 8, 9], 3) => [4, 6, 8]
([-22, 5, 3, 11, 26, -6, -7, -8, -9, -8, 26], 2) => [-8, 26]
([6, -25, 3, 7, 5, 5, 7, -3, 23], 1) => [6]
```

思路：倒序遍历整个数组，找到n个的偶数即可

代码如下：

【python】

def even_numbers(arr,n):
    ret=[]
    if n<=0:
        return ret
    for i in range(len(arr)):
        temp=arr[len(arr)-i-1]
        if temp%2==0:
            ret.insert(0,temp)
            n-=1
            if n<=0:
                break
    return ret

【C++】

std::vector<int> evenNumbers(std::vector<int> arr, int n) {
    //your code here
    std::vector<int> a;
    if (n <= 0)
    {
        return a;
    }
    int len = arr.size();
    for (int i = 0; i < arr.size(); i++)
    {
        if (arr[len-i-1] % 2 == 0)
        {
            a.insert(a.begin(), arr[len-i-1]);
            n--;
            if (n <= 0)
            {
                break;
            }
        }
    }
    return a;
}