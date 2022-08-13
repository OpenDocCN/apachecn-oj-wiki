<!--yml
category: codewars
date: 2022-08-13 11:41:23
-->

# Codewars-python 20190117_Katherine_pbq的博客-CSDN博客

> 来源：[https://blog.csdn.net/Katherine_pbq/article/details/86510214?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-11-86510214-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/Katherine_pbq/article/details/86510214?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-11-86510214-null-null.142^v40^control,185^v2^control&utm_term=codewars)

1.Descending Orders
input:324189
output:984321
知识点：’’.join
[::-1]:list倒序排列

```
def Descending_Order(num):

    num = list(str(num))
    return int(''.join(sorted(num)[::-1])) 
```

2.Your Order,please
input:“is2 Thi1s T4est 3a”
output:“Thi1s is2 3a T4est”
方法一：

```
def order(sentence):

    sentence = sentence.split()
    Arr = ['']*len(sentence)
    for s in sentence:
        for c in s:
            if c.isdigit(): 
                Arr[ord(c)-ord('1')] = s
                break
    return ' '.join(Arr) 
```

方法二：

```
def order(words):
	return ' '.join(sorted(words.split(), key=lambda w:sorted(w))) 
```

3.Mumbling
input:“abcd”
output:“A-Bb-Ccc-Dddd”
自己方法：

```
def accum(s):
	s = list(s)
	result = []
	reslut1 = []
	for i in range(len(s)):
    	result.append((i+1)*s[i])
	for j in result:
   		j = j.capitalize()
    	result1.append(j)
	return str('-'.join(result1)) 
```

大神做法：

```
def accum(s):
    return '-'.join(c.upper()+c.lower()*i for i, c in enumerate(s)) 
```

4.Find the next perfect square!

```
import math
def find_next_square(sq):

    a = math.sqrt(sq)  
    if a - int(a) > 0:
        return -1
    else:
        return int(pow((a+1),2)) 
```