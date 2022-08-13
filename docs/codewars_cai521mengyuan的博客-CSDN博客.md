<!--yml
category: codewars
date: 2022-08-13 11:30:01
-->

# codewars_cai521mengyuan的博客-CSDN博客

> 来源：[https://blog.csdn.net/cai521mengyuan/article/details/103599435?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036052916782184618183%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036052916782184618183&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-103599435-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/cai521mengyuan/article/details/103599435?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036052916782184618183%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036052916782184618183&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-103599435-null-null.142^v40^control,185^v2^control&utm_term=codewars)

### codewars:Tournament Cross Table with Sonneborn-Berger Score

```
import copy

def crosstable(players, result):
#     return (
#         "#  Player             1 2 3  Pts  SB\n"
#         "=====================================\n"
#         "1  Boris Spassky        1 =  1.5 1.25\n"
#         "2  Garry Kasparov     0   1  1.0 0.50\n"
#         "3  Viswanathan Anand  = 0    0.5 0.75")
    num_players = len(players)
    str_num = [str(i) for i in range(num_players+1)]
    str_num = ' '.join(str_num[1:])
    res = f'# Player {str_num} Pts SB\n'
    res += '==================================================\n'
    print(res)
    dict_res = {}
    for i in range(len(result)):
        sum_n = sum([0 if x==None else x for x in result[i]])
        result[i].append(sum_n)

    results = copy.deepcopy(result)
    for i in range(len(result)):
        SB_num1, SB_num2 = 0, 0
        for j in range(len(result[0])):
            if result[i][j] == 1:
                SB_num1 += result[j][-1]
            if result[i][j] == 0.5:
                SB_num2 += result[j][-1]

        results[i].append(SB_num1 + SB_num2 / 2)

    # 获取列表的下标和值
    results = sorted(enumerate(results), key=lambda x:x[1][num_players:], reverse=True)
    flag = [i[0] for i in results]

    for i in range(len(results)):
        reslist = [None] * (num_players+2)
        for j in range(len(reslist)):
            if j >= num_players:
                reslist[j] = results[i][1][j]
            else:    
                reslist[j] = results[i][1][flag[j]]
        results[i] = reslist

    for i in range(num_players):
        dict_res[players[flag[i]]] = results[i]
    for keys, values in dict_res.items():
        for i in range(len(values)):
            if values[i] == None:
                values[i] = ' '
            if values[i] == 0.5:
                values[i] = '='
            else:
                values[i] = str(values[i])
        res = str(keys) + ' '.join(values)
        print(res) 
```

输出：

```
# Player 1 2 3 4 5 6 Pts SB
==================================================

Renee Preston  = = = 1 1 3.5 7.25
Deandre Bullock=   = = = 1 3.0 6.75
Norah Underwood= =   = 1 = 3.0 6.75
George Bautista= = =   0 1 2.5 6.25
Cruz Sullivan0 = 0 1   0 1.5 4.0
Emmett Frost0 0 = 0 1   1.5 3.0 
```

和要求的结果不太一样
记录一下大概思路