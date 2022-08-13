<!--yml
category: codewars
date: 2022-08-13 11:29:16
-->

# codewars-api-client:CodewarsAPI的客户端-其它代码类资源-CSDN文库

> 来源：[https://download.csdn.net/download/weixin_42134097/16223365?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036051716781683933844%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036051716781683933844&biz_id=1&utm_medium=distribute.pc_search_result.none-task-download-2~all~first_rank_ecpm_v1~rank_v31_ecpm-9-16223365-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://download.csdn.net/download/weixin_42134097/16223365?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036051716781683933844%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036051716781683933844&biz_id=1&utm_medium=distribute.pc_search_result.none-task-download-2~all~first_rank_ecpm_v1~rank_v31_ecpm-9-16223365-null-null.142^v40^control,185^v2^control&utm_term=codewars)

Codewars API客户端 建立与Codewars API和平台进行交互的库。 安装 使用软件包管理器使用以下命令安装库。 composer require jamesrweb/codewars-api-client 基本用法 安装软件包后，我们可以创建所需的客户端。 &lt;?php declare (strict_types= 1 ); require __DIR__ . '/vendor/autoload.php' ; use CodewarsApiClient \ Client ; $ client = new Client ( "your-api-key" ); Client Client实例允许我们以一致的方式与codewars API进行交互。 方法 获取有关用户的信息 要获取有关用户的信息，可以运行： $ client -> user (string $ usern