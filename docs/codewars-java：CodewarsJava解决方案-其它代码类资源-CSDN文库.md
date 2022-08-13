<!--yml
category: codewars
date: 2022-08-13 11:30:23
-->

# codewars-java:CodewarsJava解决方案-其它代码类资源-CSDN文库

> 来源：[https://download.csdn.net/download/weixin_42134094/15780481?ops_request_misc=&request_id=&biz_id=103&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-download-2~all~sobaiduweb~default-9-15780481.142^v40^control,185^v2^control](https://download.csdn.net/download/weixin_42134094/15780481?ops_request_misc=&request_id=&biz_id=103&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-download-2~all~sobaiduweb~default-9-15780481.142^v40^control,185^v2^control)

Java解决方案 挑战性 圭 问题 8 8 6 8 6 8 7 从世纪开始 第一世纪的跨度是从1年到100年（包括100年），第二个世纪是从101年到200年（包括200年），依此类推。给定年份，返回它所在的世纪。 public class Solution { public static int century ( int number ) { // Your solution } } 解决方案public class Solution { public static int century ( int number ) { return ( int )( Math . ceil(number / 100.0 )); } } 偶数或奇数 创建一个函数，该函数以整数作为参数，并为偶数返回“ Even”或为奇数返回“ Odd”。 public cla