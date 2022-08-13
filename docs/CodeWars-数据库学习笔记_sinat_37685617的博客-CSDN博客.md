<!--yml
category: codewars
date: 2022-08-13 11:25:50
-->

# CodeWars 数据库学习笔记_sinat_37685617的博客-CSDN博客

> 来源：[https://blog.csdn.net/sinat_37685617/article/details/113684939?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036032516782184646989%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=166036032516782184646989&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-113684939-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/sinat_37685617/article/details/113684939?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036032516782184646989%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=166036032516782184646989&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-113684939-null-null.142^v40^control,185^v2^control&utm_term=codewars)

开个贴记录一下在codewars里面用到的数据函数~
先放一个[CodeWars](https://www.codewars.com/dashboard)官网链接~

> 内容都是百度大佬们+自己理解整合的

## 1、bit_length() 函数

使用实例：

```
 select id,bit_length(name) as name,birthday,bit_length(race) as race
from demographics 
```

数据库中获取长度的函数有3中：

1.  **BIT_LENGTH**：返回字符串的bit位数。
2.  **LENGTH**：返回字符串的byte数。
3.  **CHAR_LENGTH**：，返回字符串的字符数量。

由于字符集（utf-8、gbk等）编码问题（主要是中文编码），这三个函数返回的数值会有不同。
对于**一个中文字符**来说：
在 **GBK** 编码下：1个中文字符占2个字节，1个字节占8位，总bit长度16；
在 **UTF-8** 编码下：1个中文字符占3个字节，1个字节占8位，总bit长度24；
非中文字符：
1个英文字符占1个字节，1个字节占8位，一个英文字符占总bit长度8。

## 2、COALESCE 函数

这是一个处理空值的函数，nvl、isnull 为其简化函数。
其参数格式如下： COALESCE(expression,value1,value2……,valuen)
expression为需要判断的表达式，而其后的参数个数不定。 COALESCE()函数将会依次判断括号内的所有参数（包括expression），并返回第一个非空表达式。如果所有的表达式都为空值，则返回NULL。

## 3、NULLIF 函数

NULLIF(expr1,expr2)，如果expr1=expr2成立，那么返回值为null，否则返回值为expr1的值。

下面是COALESCE 和 NULLIF 结合使用的实例：

```
 select 
id,
COALESCE(nullif(name,''),'[product name not found]') as name,
price,
COALESCE(nullif(card_name,''),'[card name not found]') as card_name,
card_number,
transaction_date
from eusales
where 
price is not null 
and price > 50 
```

## 4、WITH AS 子查询

将公共的子查询部分提前到前面，用with……as……定义一个临时表并取别名，在下面具体的sql运用时引用其别名。
临时表之间用逗号分隔，只用一个with即可：

```
with
e as (select * from scott.emp),
d as (select * from scott.dept)
select * from e, d where e.deptno = d.deptno; 
```

WITH语句的优点:

(1). SQL可读性增强。子查询前置，让整句sql逻辑结构更清晰。

(2)、with子查询只执行一次，将结果存储在用户临时表空间中，可以引用多次，增强性能。

具体实例：

```
 with special_sales as(select department_id from sales where price>90)
select * from departments where id IN (select * from special_sales) 
```