<!--yml
category: codewars
date: 2022-08-13 11:35:31
-->

# codewars-solutions:Codewars的个人解决方案（https-其它代码类资源-CSDN文库

> 来源：[https://download.csdn.net/download/weixin_42121086/18465413?ops_request_misc=&request_id=&biz_id=103&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-download-2~all~sobaiduweb~default-8-18465413.142^v40^control,185^v2^control](https://download.csdn.net/download/weixin_42121086/18465413?ops_request_misc=&request_id=&biz_id=103&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-download-2~all~sobaiduweb~default-8-18465413.142^v40^control,185^v2^control)

代码战解决方案 这么多的在线算法培训平台，我的技能太差了。 无论如何，我跳进了一个新坑！ 卡塔斯 回溯与优化。 此解决方案也可以通过7x7 kata。 使用所有排列作为每一行和每一列的候选项 维护一个不可能的数字（使用位）的掩码网格，可以通过线索对其进行初始化 重复以下步骤， 通过遮罩网格过滤候选对象（如果什么都没有发生，则中断） 更新遮罩网格并尝试确认数字（如果它是其单元格/行/列中的唯一可能值） 通过回溯确认每行的排列 选择下一个候选人并检查 如果有效，则继续操作（在最后一行时解决；在第一行时无法解决） 太暴力了！！！ 请注意，如果m或n是2的幂（至少4），则可以通过相乘来计算。 然后分而治之。 简单的。 看评论。 核心算法是K-均值。 但是，如何选择正确的初始中心？ 巧合的是，标准长度（1/3/7）解决了这个问题。 简单的。 缓存操作并最终执行。 详细描述。 其实很容易。