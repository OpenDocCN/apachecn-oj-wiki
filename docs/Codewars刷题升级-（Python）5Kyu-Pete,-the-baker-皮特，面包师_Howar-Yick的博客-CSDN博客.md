<!--yml
category: codewars
date: 2022-08-13 11:41:51
-->

# Codewars刷题升级 （Python）5Kyu Pete, the baker 皮特，面包师_Howar Yick的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41432655/article/details/92801145?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-25-92801145-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_41432655/article/details/92801145?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-25-92801145-null-null.142^v40^control,185^v2^control&utm_term=codewars)

**题目描述：**

> Pete likes to bake some cakes. He has some recipes and ingredients. Unfortunately he is not good in maths. Can you help him to find out, how many cakes he could bake considering his recipes?
> 皮特喜欢烤蛋糕。他有一些食谱和原材料。不幸的是，他数学不好。你能帮他计算出，根据他的食谱，他能烤多少蛋糕吗？
> Write a function cakes(), which takes the recipe (object) and the available ingredients (also an object) and returns the maximum number of cakes Pete can bake (integer). For simplicity there are no units for the amounts (e.g. 1 lb of flour or 200 g of sugar are simply 1 or 200). Ingredients that are not present in the objects, can be considered as 0.
> 编写一个函数cakes（），它获取配方（对象）和可用成分（也是对象），并返回皮特可以烘焙的最大蛋糕数（整数）。为了简单起见，数量没有单位（例如1磅面粉或200克糖仅为1或200）。物品中不存在的成分可以被视为0。

**Examples:**
**例子：**

> must return 2 必须返回2
> cakes({flour: 500, sugar: 200, eggs: 1}, {flour:1200, sugar: 1200, eggs: 5, milk: 200})
> must return 0 必须返回0
> cakes({apples: 3, flour: 300, sugar: 150, milk: 100, oil: 100},{sugar: 500, flour: 2000, milk: 2000})

**解题思路：**

> 设定结果变量为一个很大的值，或者浮点数的无穷大float(‘inf’)，循环食谱字典的键，如果原料里有此键且原料键值除以食谱键值向下取整小于结果变量，则将取整的值赋值给结果变量，否则返回0.

**代码实现：**

```
def cakes(recipe, available):
    # TODO: insert code
    result=9999
    for i in recipe:
        if i in available:
            if result > available[i] // recipe[i]:
                result=available[i] // recipe[i]
        else:
            return 0
    return result 
```