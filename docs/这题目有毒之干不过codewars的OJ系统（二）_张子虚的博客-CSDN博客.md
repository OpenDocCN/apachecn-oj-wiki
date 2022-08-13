<!--yml
category: codewars
date: 2022-08-13 11:44:05
-->

# 这题目有毒之干不过codewars的OJ系统（二）_张子虚的博客-CSDN博客

> 来源：[https://blog.csdn.net/ccaoee/article/details/80110044?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-80110044.nonecase](https://blog.csdn.net/ccaoee/article/details/80110044?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-80110044.nonecase)

## kata

**<4kyu>Guess the Digits and Expression**
Description:
Give you a multiplication arithmetic expression:

```
 ABC
            *   CBA
            -------
            = 39483 
```

Each character represents a diffrent digit(1-9), and you need to find the arithmetic expression and return the result like this:`"123 * 321 = 39483"`

## solutions

**这是我的解决方案：**

```
function guessExpression(exp){
  let expression = ''
  const reg = /\s*(\w+)\n\*\s*(\w+)\n.*\n[\D]*(\d+)/g
  const unitArr = reg.exec(exp).slice(1)
  const [aDigit, bDigit] = unitArr
  const aDigitLast = aDigit[aDigit.length - 1]
  const bDigitLast = bDigit[bDigit.length - 1]
  const digitList = [...new Set(aDigit)]
  const numResult = parseInt(unitArr[2])
  const isOdd = numResult % 2 === 1
  function vEach(strs, stat = {}) {
    const firstStr = strs[0]
    for (let i of [1, 2, 3, 4, 5, 6, 7, 8, 9]) {
      if (expression) return
      stat[firstStr] = i
      if (strs.length > 1) {
        vEach(strs.slice(1), stat)
      } else {
        const realADigit = [].map.call(aDigit, v => stat[v]).join('')
        const realBDigit = [].map.call(bDigit, v => stat[v]).join('')
        if (realADigit[0] && realBDigit[0] && (~~realADigit * ~~realBDigit === numResult)) {

          expression = `${realADigit} * ${realBDigit} = ${numResult}`
          if (realADigit.split('').reverse().join('') === realBDigit) {
            const min = Math.min(~~realADigit, ~~realBDigit)
            const max = Math.max(~~realADigit, ~~realBDigit)
            expression = `${min} * ${max} = ${numResult}`
          }
        }
      }
    }
  }
  vEach(digitList.join(''))
  return expression
}
```

提交时报错：execution time out 12000ms
后来想到如果乘积为奇数，则两乘数也为奇数，如果乘积为偶数，则两乘数必有一个为偶数
所以有如下的优化：

```
......
const firstStr = strs[0]
    let mapArr = []
    if (isOdd) {
      if (firstStr === aDigitLast || firstStr === bDigitLast) {
        mapArr = [1, 3, 5, 7, 9]
      } else {
        mapArr = [1, 2, 3, 4, 5, 6, 7, 8, 9]
      }
    } else {
      if (firstStr === aDigitLast || firstStr === bDigitLast) {
        if (aDigitLast % 2 === 1 && firstStr !== aDigitLast) {
          mapArr = [2, 4, 6, 8]
        } else if (bDigitLast % 2 === 1 && firstStr !== bDigitLast) {
          mapArr = [2, 4, 6, 8]
        } else {
          mapArr = [1, 2, 3, 4, 5, 6, 7, 8, 9]
        }
      } else {
        mapArr = [1, 2, 3, 4, 5, 6, 7, 8, 9]
      }
    }
    for (let i of mapArr) {
      if (expression) return
    ......
```

然而并没有什么卵用，执行时间几乎和之前的算法一样。
如此，在网络上搜索相关答案，找到**某大佬的解决方案：**

```
function guessExpression(exp) {
  let m = exp.match(/([\w\d]+)/g);
  let sym = [m[0], m[1]];
  let res = +m[2];

  let uniq = (sym[0] + sym[1]).split('')
    .filter((el, i, arr) => arr.indexOf(el, i+1) === -1);

  let nums = new Array(uniq.length).fill(1);

  while (1) {
    let a = sym[0].replace(/./g, c => nums[uniq.indexOf(c)]);
    let b = sym[1].replace(/./g, c => nums[uniq.indexOf(c)]);
    if ((+a) * (+b) === res) {
      return `${a} * ${b} = ${res}`;
    }
    for (let i = 0; i < nums .length; ++i) {
      nums[i] += 1;
      if (nums[i] >= 10) {
        nums[i] = 1;
      } else {
        break;
      }
    }
  }

}
```

使用`console.time`测试了下，大佬的解法用时几乎是我解法的一半。
令人沮丧的是：codewars的OJ用大佬的解法也没有通过测试，我不知道要如何optimize my solution.

## 相关链接