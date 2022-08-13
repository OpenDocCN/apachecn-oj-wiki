<!--yml
category: codewars
date: 2022-08-13 11:28:41
-->

# 如何注册leetcode-testing-system:学生测试系统。Codewars/Hackerrank/Leetcode克隆-其它代码类资源-CSDN文库

> 来源：[https://download.csdn.net/download/weixin_38665411/19952557?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036051116782395389599%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036051116782395389599&biz_id=1&utm_medium=distribute.pc_search_result.none-task-download-2~all~first_rank_ecpm_v1~rank_v31_ecpm-29-19952557-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://download.csdn.net/download/weixin_38665411/19952557?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036051116782395389599%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036051116782395389599&biz_id=1&utm_medium=distribute.pc_search_result.none-task-download-2~all~first_rank_ecpm_v1~rank_v31_ecpm-29-19952557-null-null.142^v40^control,185^v2^control&utm_term=codewars)

如何注册leetcode 关于项目 它是 codewars/hackerrank/leetcode 的克隆，但适用于我大学的学生演示： 管理员凭据： admin:admin 常用用户凭据： user:user 如何使用 以管理员身份登录 创建学生组 创建学生 创建任务和测试 将不同的任务合并为一项工作 就这样。 以普通用户身份登录并享受编码 linux下如何设置 克隆 repo git clone 安装依赖npm install 构建前端npm run build:client 构建后端npm run build:server 安装 PostgreSQL 使用来自dist/backend/server/db setup和init脚本初始化数据库 配置nginx以从dist/frontend服务dist/frontend 将/api路由的 nginx proxy_pass添加proxy_pass后端监听的地址（默认为localhost:5000 ） 使用config.json配置服务器 跑步 现在您可以使用节点运行服务器： cd dist/backend/server && node -