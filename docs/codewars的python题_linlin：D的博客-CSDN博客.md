<!--yml
category: codewars
date: 2022-08-13 11:41:35
-->

# codewars的python题_linlin:D的博客-CSDN博客

> 来源：[https://blog.csdn.net/saroyamal/article/details/119674811?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-17-119674811-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/saroyamal/article/details/119674811?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-17-119674811-null-null.142^v40^control,185^v2^control&utm_term=codewars)

随便做几个

# 8kyu

## descending order

```
def Descending_Order(num):
    if isinstance(num, int) and num >= 0:
        return int(''.join(sorted(str(num),reverse=True)))
    else:
        raise ValueError('Non-negative integer expected') 
```

相关函数：
isinstance()
.join()
sorted()
str()
[::-1]

```
def Descending_Order(num):
    return int(''.join(sorted(str(num))[::-1])) 
```

```
Descending_Order = lambda n: int(''.join(reversed(sorted(str(n))))) 
```

lambda函数
sum = lambda arg1, arg2: arg1 + arg2
调用sum函数
print ("相加后的值为 : ", sum( 10, 20 ))
print ("相加后的值为 : ", sum( 20, 20 ))

# 7kyu

## Square Every Digit

```
def square_digits(num):
    return int(''.join(str(int(d)**2) for d in str(num))) 
```

for函数的位置注意一下

## Unique In Order

itertools.groupby

```
from itertools import groupby

def unique_in_order(iterable):
    return [k for (k, _) in groupby(iterable)] 
```

## Break camelCase

```
import re

def solution(s):
    return re.sub(r"\B([A-Z])", r" \1", s) 
```

```
def solution(s):
    return ''.join(' ' + c if c.isupper() else c for c in s) 
```

# 6kyu

## Stop gninnipS My sdroW!

```
def spin_words(sentence):
    return " ".join(x[::-1] if len(x)>4 else x for x in sentence.split(' ')) 
```

这种LC结构很重要。

# 5kyu

## Simple Pig Latin

```
def pig_it(text):
    return ' '.join(x[1:]+x[0]+"ay" if x.isalpha() else x for x in text.split()) 
```

都是一类题。

# 4kyu

## A Simplistic TCP Finite State Machine (FSM)

别人的解法，很好：

```
def traverse_TCP_states(events):
    state = "CLOSED"  # initial state, always
    # state:event
    INITIAL_EVENT = {
        "CLOSED: APP_PASSIVE_OPEN":['LISTEN'],
        "CLOSED: APP_ACTIVE_OPEN" :['SYN_SENT'],
        "LISTEN: RCV_SYN": ['SYN_RCVD'],
        "LISTEN: APP_SEND": ['SYN_SENT'],
        "LISTEN: APP_CLOSE": ['CLOSED'],
        "SYN_RCVD: APP_CLOSE":['FIN_WAIT_1'],
        "SYN_RCVD: RCV_ACK":['ESTABLISHED'],
        "SYN_SENT: RCV_SYN": ['SYN_RCVD'],
        "SYN_SENT: RCV_SYN_ACK":['ESTABLISHED'],
        "SYN_SENT: APP_CLOSE": ['CLOSED'],
        "ESTABLISHED: APP_CLOSE": ['FIN_WAIT_1'],
        "ESTABLISHED: RCV_FIN":['CLOSE_WAIT'],
        "FIN_WAIT_1: RCV_FIN":['CLOSING'],
        "FIN_WAIT_1: RCV_FIN_ACK":['TIME_WAIT'],
        "FIN_WAIT_1: RCV_ACK":['FIN_WAIT_2'],
        "CLOSING: RCV_ACK":['TIME_WAIT'],
        "FIN_WAIT_2: RCV_FIN": ['TIME_WAIT'],
        "TIME_WAIT: APP_TIMEOUT":['CLOSED'],
        "CLOSE_WAIT: APP_CLOSE": ['LAST_ACK'],
        "LAST_ACK: RCV_ACK": ['CLOSED']
    }
    def get_key(value):
        dic=INITIAL_EVENT
        return [k for (k,v) in dic.item() if value in v]
    def get_value(key):
        dic=INITIAL_EVENT
        return [v for (k,v) in dic.items() if k == key]

    if ['APP_PASSIVE_OPEN','APP_ACTIVE_OPEN'].count(events[0]) == 1:
        for i in events:
            event = '' +state + ': ' + i + ''
            if bool(get_value(event))==True:
                state=get_value(event)[0][0]
            else:
                return('ERROR')
    else:
        return('ERROR')
    return get_value(event)[0][0] 
```