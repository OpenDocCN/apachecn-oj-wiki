<!--yml
category: codewars
date: 2022-08-13 11:41:07
-->

# codewars-strings mix_跳舞的巴比伦的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41136897/article/details/104202855?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-104202855-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_41136897/article/details/104202855?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-104202855-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## Strings Mix

原题目链接：https://www.codewars.com/kata/5629db57620258aa9d000014/python

```
import string
def mix(s1, s2):
    d1 = {}
    for i in string.ascii_lowercase:
        n1, n2 = s1.count(i), s2.count(i)
        if max(n1, n2) > 1:
            c1 = '1' if n1 > n2 else '2' if n2 > n1 else '='
            d1[i] = (-max(n1, n2), c1 + ':' + i * max(n1, n2))
    return '/'.join(d1[i][1] for i in sorted(d1, key=lambda x: d1[x])) 
```

### 思路

1.按照a-z的顺序遍历一遍所有的小写字母，然后得到每个字母在字符串里面的出现次数n1, n2。（相当于滤除了特殊字符以及大写字母）
2.得到n1, n2的最大值，与一比较，就可以滤除出现次数为零或者一的字母。
3.设置常量c1，保存字母在哪一个字符串里面出现的次数最多（1或2），出现次数相同时，即为=。
4.将对应字母设为d1的一个key，value为一个tuple。tuple例如(-4, ‘1:aaaa’)，第一个值为出现次数的相反数（用于排序），第二个值为组合好的字符串，用于显示出现在哪一个字符串和出现的次数。
5.sorted()函数接收了两个参数，一个是需要排序的迭代对象d1，一个是排序的参照函数，lambda x: d1[x] 的意思就是该匿名函数根据每个键的键值来排序，键值为一个元组， 先根据第一个数来排序，第一个数相同时再根据组合好的字符串排序。
6.根据最后的生成器来完成一个字符串。

### 注意事项

1.基本的排序顺序应该主要是
（1）字母出现次数从大到小
（2）在两个字符串里面出现的次数是否相同
（3）按照a-z的顺序排列
2.先按照a-z的顺序遍历时，解决了（3）。
3.sorted排序时，会把出现次数最少的放在最前（从小到大），因此用了相反数来反向排序。（调用reverse参数应该也可以）
4.两个字母出现次数相同时，要求把出现次数相同的字母放在最后，反应在键值tuple的第二个值（字符串）的比较，这里涉及到了字符串的比较，默认是按照字符的ASCII的大小比较的，所以’=’ > ‘1’或’2’，所以带有’='的字符串会被放到后面。

***若有不足之处 希望各位评论里提出***