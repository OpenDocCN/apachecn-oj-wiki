<!--yml
category: codewars
date: 2022-08-13 11:49:56
-->

# Kata | Codewars 之 Find the stray number_lin_________的博客-CSDN博客

> 来源：[https://blog.csdn.net/lin_________/article/details/119991711?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-119991711.nonecase](https://blog.csdn.net/lin_________/article/details/119991711?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-119991711.nonecase)

> Title:
> 
> You are given an *odd-length* array of integers, in which all of them are the same, except for one single number.
> 
> Complete the method which accepts such an array, and returns that single different number.
> 
> **The input array will always be valid!** (odd-length >= 3)
> 
> ## Examples
> 
> ```
> [1, 1, 2] ==> 2
> [17, 17, 3, 17, 17, 17, 17] ==> 3
> ```

 我的：

```
#include <vector>
#include <iostream>
#include <math.h>
using namespace std;
int stray(std::vector<int> numbers){
	if (numbers.size() / 2 == 0 && numbers.size()<3 ) {
		return 0;
	}
	else
	{
		sort(numbers.begin(), numbers.end());
		vector<int>::iterator iter;
		for (iter = numbers.begin(); iter != numbers.end(); iter++) {
			if (numbers[0] == numbers[1]) {
				return numbers.back();
			}
			else {
				return numbers.front();
			}
		}
	}
	return 0;
```

 高手：

```
#include <algorithm>

int stray(std::vector<int> numbers) 
{
  std::sort(numbers.begin(), numbers.end());
  return (numbers[0] != numbers[1]) ? numbers.front() : numbers.back();
};
```

 （想到了三目但是没有用）