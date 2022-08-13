<!--yml
category: codewars
date: 2022-08-13 11:34:33
-->

# codewars——Pick peaks_熊熊玩python的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41552148/article/details/100172178?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-100172178.142^v40^control,185^v2^control](https://blog.csdn.net/weixin_41552148/article/details/100172178?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-100172178.142^v40^control,185^v2^control)

> In this kata, you will write a function that returns the positions and the values of the “peaks” (or local maxima) of a numeric array.For example, the array arr = [0, 1, 2, 5, 1, 0] has a peak at position 3 with a value of 5 (since arr[3] equals 5).The output will be returned as an object of type PeakData which has two members: pos and peaks. Both of these members should be vectors. If there is no peak in the given array then the output should be a PeakData with an empty vector for both the pos and peaks members.PeakData is defined in Preloaded as follows:struct PeakData {
> vector pos, peaks;
> };Example: pickPeaks([3, 2, 3, 6, 4, 1, 2, 3, 2, 1, 2, 3]) should return {pos: [3, 7], peaks: [6, 3]} (or equivalent in other languages)All input arrays will be valid integer arrays (although it could still be empty), so you won’t need to validate the input.The first and last elements of the array will not be considered as peaks (in the context of a mathematical function, we don’t know what is after and before and therefore, we don’t know if it is a peak or not).Also, beware of plateaus !!! [1, 2, 2, 2, 1] has a peak while [1, 2, 2, 2, 3]does not. In case of a plateau-peak, please only return the position and value of the beginning of the plateau. For example: pickPeaks([1, 2, 2, 2, 1]) returns {pos: [1], peaks: [2]} (or equivalent in other languages)Have fun!

> 例如，数组arr=[0，1，2，5，1，0]在位置3处有一个峰值，值为5（因为arr[3]等于5）。
> 输出将作为peakdata类型的对象返回，peakdata有两个成员：pos和peaks。这两个成员都应该是向量s。如果给定数组中没有峰值，那么输出应该是一个峰值数据，pos和peaks成员都有一个空向量。
> 峰值数据在预加载中定义如下：
> 结构峰值数据{
> 向量pos，峰值；
> }；
> 示例：pickpeaks（[3、2、3、6、4、1、2、3、2、1、2、3]）应返回pos:[3、7]，peaks:[6、3]（或其他语言中的等效值）
> 所有输入数组都将是有效的整数数组（尽管它可能仍然为空），因此您不需要验证输入。
> 数组的第一个和最后一个元素不会被视为峰值（在数学函数的上下文中，我们不知道什么在后面和前面，因此我们不知道它是否是峰值）。
> 同时，小心高原！！！！[1，2，2，2，1]有峰值，而[1，2，2，3]没有。如果出现高原峰值，请只返回高原起点的位置和值。例如：pickpeaks（[1，2，2，1]）返回pos:[1]，peaks:[2]（或其他语言中的等效值）
> 玩得高兴！

# 我的思路

我的思路是这样的哈：

1.  遍历数组，设定一个起始的key值，初始值为0，当每个值比左边的大，就+1，比右边的小呢就再+1，当值为2时返回。每次循环结束，把key重置为0
2.  上面的算法实现了返回部分峰值，即一个数左右两边都比他小的这种情况，没有考虑右边的数与他相等。题目要求返回峰值的第一个index
3.  因此，我设置count的值，只要右边的数和它本身相等，那就设定count+1，直到出现第比他还小的数，这个时候i - count就是第一次出现的数字咯。

```
def pick_peaks(arr):
    dic = dict()
    dic['pos'] = list()
    dic['peaks'] = list()
    key = 0
    count = 0
    for i in range(1, len(arr)-1):
        if arr[i] > arr[i-1]:
            key += 1
        if arr[i] > arr[i+1]:
            key += 1
        if arr[i] == arr[i+1]:
            count += 1
            continue
        if key == 2:
            dic['pos'].append(i-count)
            dic['peaks'].append(arr[i])
        key = 0
        count = 0
    print(dic)
    return dic 
```

# 我的总结

本来想用C++来做，练习C++，后来发现C++的话，我连题目都看不懂，所以改为python了。做出来就好，做出来就好。