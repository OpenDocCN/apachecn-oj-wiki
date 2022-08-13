<!--yml
category: codewars
date: 2022-08-13 11:37:46
-->

# Codewars 刷题笔记（Python）3.Friend or Foe_apollo315的博客-CSDN博客

> 来源：[https://blog.csdn.net/apollo315/article/details/104644062?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-7-104644062-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/apollo315/article/details/104644062?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-7-104644062-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## 题目

Make a program that filters a list of strings and returns a list with only your friends name in it.

If a name has exactly 4 letters in it, you can be sure that it has to be a friend of yours! Otherwise, you can be sure he’s not…

Ex: Input = [“Ryan”, “Kieran”, “Jason”, “Yous”], Output = [“Ryan”, “Yous”]

i.e.

```
friend ["Ryan", "Kieran", "Mark"] `shouldBe` ["Ryan", "Mark"] 
```

Note: keep the original order of the names in the output.

> 难度：7 kyu

## 我的解法1：错误

```
def friend(x):
    for item in x:
        if len(item) != 4:
            x.remove(item)
    return x 
```

开始我不明白到底哪里出错了，想了半天想不通，只好换了一种方法通过了题目，然后去讨论区看了下，发现很多人都犯了这个错，说明是比较经典的一个坑。

原因其实是因为for循环是按索引值迭代循环，每次索引值+1，但是`remove`函数如果操作了列表会导致列表索引变动，而for循环还是傻傻的按照原来的索引值+1来迭代，这样就可能跳过一些值，最终导致结果错误。你可以给代码加上`print`打印出来操作过程或结果，更直观的感受下。

> 我这里说的比较简略，如果不明白的话可以参考[Python中.remove()的一个坑](https://blog.csdn.net/weixin_41822375/article/details/86697648)，里边有具体的例子帮助理解。

评论区有个经典的建议：

> it’s not right to mutate a list where you’re running a loop with it

这是一个<font>原则：不要在循环中转换列表（删除元素等操作）！</font>

建议方法：可以copy出来一个列表，一个个元素的判断操作，这样不会因原列表的索引值变动从而导致错误。

## 我的解法2：正确

```
def friend(x):
    names = []
    for name in x:
        if len(name) == 4:
            names.append(name)
    return names 
```

我们用另外一个列表names来存放结果，将原列表中长度为4的字符串都筛选出来，依次加入names列表即可。

## 更优解法

```
def friend(x):
  return [i for i in x if len(i) == 4] 
```

这是我看到的最优解法，又是一行代码搞定，做了几道题，严重怀疑7 kyu级别的是不是都能用一行代码解决啊（笑）。

这里运用了列表生成式的写法，算是Python的一种高级特性，可以简化代码，语法也不难，可以参考廖雪峰的Python教程：[列表生成式](https://www.liaoxuefeng.com/wiki/1016959663602400/1017317609699776)

## 学习总结

1.  列表的`remove`函数的一个坑：不要在for循环中使用，因为可能跳过一些值。
    <font>原则：不要在循环中转换列表（删除元素等操作）！</font>
2.  较简单的for循环考虑是否可用列表生成式来代替，简化代码。