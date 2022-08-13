<!--yml
category: codewars
date: 2022-08-13 11:40:32
-->

# tiny-three-pass-compiler-codewars:三遍编译器，可将一种简单的编程语言转换为一种小型汇编语言-其它代码类资源-CSDN文库

> 来源：[https://download.csdn.net/download/weixin_42126274/18272723?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=1&utm_medium=distribute.pc_search_result.none-task-download-2~all~first_rank_ecpm_v1~rank_v31_ecpm-21-18272723-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://download.csdn.net/download/weixin_42126274/18272723?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059016780357231535%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059016780357231535&biz_id=1&utm_medium=distribute.pc_search_result.none-task-download-2~all~first_rank_ecpm_v1~rank_v31_ecpm-21-18272723-null-null.142^v40^control,185^v2^control&utm_term=codewars)

微小的三遍编译器 将简单的编程语言转换为小的汇编语言的三遍编译器- 此存储库中的整个代码和测试将在两天内（从字面上讲，在我周末有空的时候）实施。 所以，当然，有一些我不知道的错误，但是我也没有时间去修复它们：) 怎么玩 只需通过npm安装此软件包，然后调用ttpc命令。 第一个参数是程序本身的源代码。 第二个参数是为你的源代码的参数列表（通过分离, ）。 ttpc " [ x ] x + 10 " " 50 " ttpc " [ x ] x + 500 - 10 * 20 / 2 " " 100 " 这个怎么运作 关于每个阶段的几句话。 代币 一切都始于词法单元-记号。 它的实现很简单。 令牌结构仅保存令牌的类型及其源代码中的值。 扫描器 扫描程序是一类需要输入源代码的类。 它存储光标的当前位置以及光标当前指向的当前char。 在扫描程序实例上调用getNextToken ，它消耗的