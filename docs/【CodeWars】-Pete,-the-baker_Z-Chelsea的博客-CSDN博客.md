<!--yml
category: codewars
date: 2022-08-13 11:41:47
-->

# 【CodeWars】 Pete, the baker_Z Chelsea的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_51047199/article/details/120236484?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-23-120236484-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_51047199/article/details/120236484?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-23-120236484-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# CodeWars 里的5kyu题目 Pete，the baker

题目说明：
Description:
Pete likes to bake some cakes. He has some recipes and ingredients. Unfortunately he is not good in maths. Can you help him to find out, how many cakes he could bake considering his recipes?

Write a function cakes(), which takes the recipe (object) and the available ingredients (also an object) and returns the maximum number of cakes Pete can bake (integer). For simplicity there are no units for the amounts (e.g. 1 lb of flour or 200 g of sugar are simply 1 or 200). Ingredients that are not present in the objects, can be considered as 0.

Examples:

### must return 2

cakes({flour: 500, sugar: 200, eggs: 1}, {flour: 1200, sugar: 1200, eggs: 5, milk: 200})

### must return 0

cakes({apples: 3, flour: 300, sugar: 150, milk: 100, oil: 100}, {sugar: 500, flour: 2000, milk: 2000})

Python 解决方法：
采用循环，整除，取最小值的方式
代码：

```
def cakes(recipe, available):
    sum = []
    for co in recipe.keys():
        for m in available.keys():
            if co == m:
                d = available[m]//recipe[co]
                sum.append(d)
    if len(sum) < len(recipe):
        return 0
    return min(sum)

recipe = {"flour": 500, "sugar": 200, "eggs": 1}
available = {"flour": 1200, "sugar": 1200, "eggs": 5, "milk": 200}
print(cakes(recipe, available)) 
```