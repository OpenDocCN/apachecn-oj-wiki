<!--yml
category: codewars
date: 2022-08-13 11:42:31
-->

# 【CodeWars - SQL】（8 kyu） Is n divisible by x and y?_奶糖微咸的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_37274756/article/details/123905937?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-16-123905937-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_37274756/article/details/123905937?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-16-123905937-null-null.142^v40^control,185^v2^control&utm_term=codewars)

```
关键技术： SQL
作者：奶糖不甜🍬
撰写时间：2022.4.1 
```

```
 SQL (Structured Query Language) 是具有数据操纵和数据定义等多种功能的数据库语言，这种语言具有交互性特点，能为用户提供极大的便利，数据库管理系统应充分利用SQL语言提高计算机应用系统的工作质量与效率。SQL语言不仅能独立应用于终端，还可以作为子语言为其他程序设计提供有效助力，该程序应用中，SQL可与其他程序语言一起优化程序功能，进而为用户提供更多更全面的信息。 
```

### Is n divisible by x and y?（n 能被 x 和 y 整除吗?）

##### Grade（等级）： < 8 kyu >

##### Question（题目）：

Create a function that checks if a number n is divisible by two numbers x AND y. All inputs are positive, non-zero digits.

创建一个函数来检查数字n是否能被两个数字 x 和 y 整除。所有的输入都是正数，非零数字。

##### PostgreSQL 13.0

```
select id, case when n % x = 0 and n % y = 0 then true else false end as res from kata 
```

##### SQLite 3.2.8

```
暂时没写好，后面补 
```

[CodeWars（代码战争）](https://www.codewars.com/)