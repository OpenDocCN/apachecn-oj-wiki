<!--yml
category: codewars
date: 2022-08-13 11:47:18
-->

# Codewars❤️‍_immortal12的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_40721337/article/details/113819398?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-113819398.nonecase](https://blog.csdn.net/qq_40721337/article/details/113819398?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-113819398.nonecase)

leetcode好难，codewars简单一点，不想做实验的时候玩一下这个，升级打怪。
好喜欢刷题，各种题，英语题，算法题，总之只要是一段很短的时间内能完成的事情，我都很喜欢。
而科研也需要这样**短期就能获得的成就感**，怎么做到呢？看完一篇论文，做完一个改进的实验，写完一篇博客，写完一次周报，做完一个PPT，讲完一次汇报 ，而后都能获得这样的成就感吧。

> I picture myself flying in the sky
> 'Cause I’m a bird I’m not a lie

> 不能再弄了，看论文去。
> 下午7:15，2021年2月16日（星期二）
> ![在这里插入图片描述](img/91cdf0bb7f40e44b017f8d75eb1fc385.png)

### Product of consecutive Fib numbers

Aim：prod=fn[n] * fn[n+1]
思路：设置2个变量，当前的value（current_value），当前的index（n）。

```
def productFib(prod):
    current_value=0
    n=0
    fn=[0,1]
    while current_value<prod:
        fn=fib(n)
        n+=1
        current_value=fn[-2]*fn[-1]
    if current_value==prod:
        return [fn[-2],fn[-1],True]
    else:
        return [fn[-2],fn[-1],False]

# 具有n+2个元素的Fibonacci数列
def fib(n):
    fn=[0,1]
    for i in range(n):
        temp=fn[-2]+fn[-1]
        fn.append(temp)
    return fn 
```

### Sum of Digits / Digital Root

Aim：335 ➡️ 11 ➡️ 2
笔记：list(map(int, list(str(n))))# list中的str转int

```
def digital_root(n):
    print(n)
    current_length=len(list(str(n)))
    while current_length>1:
        n=sum(list(map(int, list(str(n)))))# list中的str转int
        current_length=len(list(str(n)))
    return n 
```

### Tribonacci Sequence

笔记：too easy，注意考虑所有情况（如n<=3）

```
def tribonacci(signature, n):
    if n==0:
        return []
    elif n<=3:
        return signature[:n]
    else:
        while len(signature)<n:
            last_value=sum(signature[-3:])
            signature.append(last_value)
        return signature 
```

### Maximum subarray sum

Aim：[−2, 1, −3, 4, −1, 2, 1, −5, 4] ➡️ [4, −1, 2, 1] ➡️ 6
笔记：2次循环计算量太大，设置3个变量，i是当前值，current是当前subarray的和，max存储subarray的最大和。感觉还不太懂1次循环的方法。

```
def max_sequence(arr):
	neg=[i for i in arr if i < 0]
	if not len(neg):# list is made up of only positive numbers
		return sum(arr)
	elif len(neg)==len(arr):# list is made up of only negtive numbers
		return 0
	else:
		max,current=0,0
		for i in arr:
			current+=i
			if current<0:current=0# 从正数开始
			if current>max:max=current
		return max 
```

### Sum of pairs

Aim：在列表ints中找2个数，它们的和等于s。
笔记：1.把i作为当前循环的index，找到就停止，节约时间；2.用set()进行查询操作，而不是list，这个技巧在后面的题（Is my friend cheating）中也用到了。

```
# def sum_pairs(ints, s):
#     result=[]
#     flag=9e15
#     for i,v1 in enumerate(ints):
#         for j,v2 in enumerate(ints[i+1:]):
#             current=v1+v2
#             if current==s:
#                 if j<flag:
#                     flag=j
#                     result=[v1,v2]
#     if result==[]:
#         return None
#     else:
#         return result

# 把i作为当前循环的index，找到就停止，节约时间
def sum_pairs(ints, s):
    cache = set()
    for i in ints:
        other = s - i
        if other in cache:
            return [other, i]
        cache.add(i) 
```

### Scramblies

笔记：‘text’.count(‘t’)=2

```
def scramble(s1, s2):
    flag=True
    for i in set(s2):
        if s1.count(i) < s2.count(i):
            flag=False
    return flag 
```

### Pete, the baker

笔记：在for循环中return一次以后，程序就结束了🔚 。注意考虑特殊情况：if i in available.keys()。

```
# return后循环就停止了
def cakes(recipe, available):
    min_=9e5
    flag=True# 判断有没有缺少recipe的食材
    for i in list(recipe.keys()):
        if i in available.keys():
            temp=int(available[i]/recipe[i])
#             print(i,temp)
            if min_>temp:
                min_=temp
        else:
            flag=False
    if min_!=9e5 and flag:
    	return min_
    else:
    	return 0 
```

### int32 to IPv4

笔记：从后往前得到octet，因为二进制编码前面缺位可以补0

```
def int32_to_ip(int32):
    ip_2=bin(int32)[2:]# 10进制➡️二进制
    if len(ip_2)<=8:  
        ip_10=int(ip_2,2)
        return "0.0.0.{}".format(ip_10)
    # 从后往前，因为前面缺位可以补0
    elif 8<len(ip_2)<=16:
        octet1=ip_2[:-8]
        ip_10_1=int(octet1,2)
        octet2=ip_2[-8:]
        ip_10_2=int(octet2,2)
        return "0.0.{}.{}".format(ip_10_1,ip_10_2)
    elif 8*2<len(ip_2)<=8*3:
        octet1=ip_2[:-16]
        ip_10_1=int(octet1,2)
        octet2=ip_2[-16:-8]
        ip_10_2=int(octet2,2)
        octet3=ip_2[-8:]
        ip_10_3=int(octet3,2)
        return "0.{}.{}.{}".format(ip_10_1,ip_10_2,ip_10_3)
    elif 8*3<len(ip_2)<=8*4:
        octet1=ip_2[:-24]
        ip_10_1=int(octet1,2)
        octet2=ip_2[-24:-16]
        ip_10_2=int(octet2,2)
        octet3=ip_2[-16:-8]
        ip_10_3=int(octet3,2)
        octet4=ip_2[-8:]
        ip_10_4=int(octet4,2)
        return "{}.{}.{}.{}".format(ip_10_1,ip_10_2,ip_10_3,ip_10_4) 
```

### A Chain adding function

Aim：add(1)(2)(3)=6
笔记：__call__函数使得AddClass成为可调用函数

```
class AddClass(int):
    def __call__(self, v):#__call__函数使得AddClass成为可调用函数
        return AddClass(self + v)

def add(v):
	return AddClass(v) 
```

### Is my friend cheating?

笔记：借鉴Sum of pairs的思想，把j算出来，再在set()中进行查询操作。

```
def remov_nb(n):
    return_set=set()
    remain_set=set()
    l=[i for i in range(1,n+1)]
    sum_=sum(l)
    # i和j分别是两个乘数，通过sum_和i来代表j，再在set()中查询j。set的查询比list的查询更高效
    for i in l:
        j=(sum_-i)/(i+1)
        if j in remain_set:
            return_set.add((i,int(j))) #向set添加元组
            return_set.add((int(j),i))
        remain_set.add(i) 
    return sorted(list(return_set)) 
```