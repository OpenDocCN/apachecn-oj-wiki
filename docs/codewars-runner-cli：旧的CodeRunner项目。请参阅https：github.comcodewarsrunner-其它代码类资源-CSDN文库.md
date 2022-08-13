<!--yml
category: codewars
date: 2022-08-13 11:38:47
-->

# codewars-runner-cli：旧的CodeRunner项目。请参阅https：github.comcodewarsrunner-其它代码类资源-CSDN文库

> 来源：[https://download.csdn.net/download/weixin_42165018/15374298?ops_request_misc=&request_id=&biz_id=103&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-download-2~all~sobaiduweb~default-8-15374298.142^v40^control,185^v2^control](https://download.csdn.net/download/weixin_42165018/15374298?ops_request_misc=&request_id=&biz_id=103&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-download-2~all~sobaiduweb~default-8-15374298.142^v40^control,185^v2^control)

已归档 请使用报告任何与语言相关的问题。 关于 和先前使用该项目来使用各种测试框架以各种语言执行少量代码集。 每次运行代码时，都会在Docker容器中执行该代码，以确保执行不安全的代码。 所有执行都在Docker中完成，每个容器中都包含一个Node CLI应用程序，该应用程序管理该特定语言环境的代码执行并通过stdout返回结果。 会费 该项目是开源的，因此Codewars和Qualified社区可以为新语言和框架提供支持。 有关当前支持哪些语言以及在何处添加了Codewars / Qualified支持的更多信息，请参见“。 基本用法 每个Docker映像中都有一个Node可执行文件的副本和一个run脚本。 该脚本接受用于执行代码的多个选项。 例如，运行一个简单JavaScript脚本，它将输出2 ： # this is how you run the Node CLI. For t