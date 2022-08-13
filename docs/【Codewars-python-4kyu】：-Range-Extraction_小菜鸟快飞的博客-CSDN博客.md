<!--yml
category: codewars
date: 2022-08-13 11:49:39
-->

# 【Codewars python 4kyu】: Range Extraction_小菜鸟快飞的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36362028/article/details/100547679?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-100547679.nonecase](https://blog.csdn.net/qq_36362028/article/details/100547679?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-100547679.nonecase)

# 问题描述：

A format for expressing an ordered list of integers is to use a comma separated list of either

*   individual integers
*   or a range of integers denoted by the starting integer separated from the end integer in the range by a dash, '-'. The range includes all integers in the interval including both endpoints. It is not considered a range unless it spans at least 3 numbers. For example ("12, 13, 15-17")

Complete the solution so that it takes a list of integers in increasing order and returns a correctly formatted string in the range format.

**Example:**

```
solution([-6, -3, -2, -1, 0, 1, 3, 4, 5, 7, 8, 9, 10, 11, 14, 15, 17, 18, 19, 20])
# returns "-6,-3-1,3-5,7-11,14,15,17-20"
```

*Courtesy of rosettacode.org*

# *代码实现：*

```
#codewars第十九题
def solution(args):
    my_list = []
    my_index = 0
    i = 0
    _length = len(args)
    if _length < 3: return args
    while i < _length:
        now_index = i
        j = i + 1
        while j <= _length:  # =_length去解决最后超出长度导致跳出循环  最后几个字符无法解决的情况
            if j != _length and args[j] == args[j-1] + 1:  # j != _length and 防止超出索引寻址
                j += 1
            else:
                if j >= (now_index + 3):
                    my_list.append(str(args[now_index])+'-'+str(args[j-1])) #追加到末尾
                    my_index += 1
                    i = j - 1

                    break
                else:
                    my_list[my_index:] = args[i:j]  #切片赋值
                    my_index += (j - i)  #存储list的下一个存储下标
                    i = j - 1
                    break
        i += 1
    return ','.join(map(str,my_list))  #将list转换为字符串
solution([-6,-3,-2,-1,0,1,3,4,5,7,8,9,10,11,14,15,17,18,19,20])
#solution([-3,-2,-1,2,10,15,16,18,19,20])

#另解一
def solution(args):
    result = []
    tmp = []
    for i in args+[""]:
        if not tmp:
            tmp.append(i)
        elif i==tmp[-1]+1:
            tmp.append(i)
        else:
            if len(tmp)>=3:
                t = '{}-{}'.format(tmp[0],tmp[-1])
                result.append(t)
            else:
                result.extend(tmp)            
            tmp = []
            tmp.append(i)
    #print(','.join(map(str,result)))
    return ','.join(map(str,result))

#另解二
def solution(args):
    out = []
    beg = end = args[0]

    for n in args[1:] + [""]:        
        if n != end + 1:
            if end == beg:
                out.append( str(beg) )
            elif end == beg + 1:
                out.extend( [str(beg), str(end)] )
            else:
                out.append( str(beg) + "-" + str(end) )
            beg = n
        end = n

    return ",".join(out)
solution([-6,-3,-2,-1,0,1,3,4,5,7,8,9,10,11,14,15,17,18,19,20])
```