<!--yml
category: codewars
date: 2022-08-13 11:52:25
-->

# 每日一道codewars题之移动数组中所有0至数组尾部_weixin_33778778的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_33778778/article/details/91460552?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-91460552.nonecase](https://blog.csdn.net/weixin_33778778/article/details/91460552?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-91460552.nonecase)

> 我好像只能写出来这三种方法，但是总感觉能用`sort`方法搞定，如果大佬们有更好的方法，希望不吝赐教评论告诉我哈?

## 题目

编写一个算法，该算法采用数组并将所有零移动到最后，保留其他元素的顺序。 (Write an algorithm that takes an array and moves all of the zeros to the end, preserving the order of the other elements.)

```
moveZeros([false,1,0,1,2,0,1,3,"a"]) 
复制代码
```

## 方法一

使用`reduce`方法，建立一个临时数组存储0，当当前元素是0的时候就push进临时数组，不为0就return进结果数组，最后拼接两个数组

```
const moveZeros = arr => {
  let temp = []
  let data = arr.reduce((pre, cur) => {
    if (cur !== 0) return [...pre, cur]
    else {
      temp.push(cur)
      return [...pre]
    }
  }, [])
  return data.concat(temp)
}
复制代码
```

## 方法二

使用`filter`过滤出所有非0的数据，然后再使用Array.fill填充0

```
const moveZeros = arr => {
  let data = arr.filter(ele => ele !== 0)
  return data.concat(new Array(arr.length - data.length).fill(0))
}
复制代码
```

## 方法三

使用`filter`过滤出所有非0的数据，然后再`filter`出来等于0的 再`concat`

```
const moveZeros = arr => arr.filter(ele => ele !== 0).concat(arr.filter(ele => ele === 0))
复制代码
```

## 总结

这题好像真的很简单，哈哈毕竟只有`5kyn`。 最后附上题目链接和codewars地址