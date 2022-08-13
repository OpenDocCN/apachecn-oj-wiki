<!--yml
category: codewars
date: 2022-08-13 11:30:55
-->

# codewars-sql:CodewarsSQL解决方案-其它代码类资源-CSDN文库

> 来源：[https://download.csdn.net/download/weixin_42109125/15648504?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036052916782184618183%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036052916782184618183&biz_id=1&utm_medium=distribute.pc_search_result.none-task-download-2~all~first_rank_ecpm_v1~rank_v31_ecpm-25-15648504-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://download.csdn.net/download/weixin_42109125/15648504?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036052916782184618183%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036052916782184618183&biz_id=1&utm_medium=distribute.pc_search_result.none-task-download-2~all~first_rank_ecpm_v1~rank_v31_ecpm-25-15648504-null-null.142^v40^control,185^v2^control&utm_term=codewars)

SQL解决方案 挑战性 圭 问题 简单 中等的 难的 8 :star: 偶数或奇数 您将得到一张表格， numbers ，一列number 。 返回一个表，该表的is_even列包含“ Even”或“ Odd”，具体取决于number列的值。 数字表架构：数字INT 输出表模式：is_even STRING 解决方案SELECT CASE WHEN number % 2 = 0 THEN ' Even ' ELSE ' Odd ' END AS is_even FROM numbers;