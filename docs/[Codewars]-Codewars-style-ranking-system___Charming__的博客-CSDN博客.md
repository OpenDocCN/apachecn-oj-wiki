<!--yml
category: codewars
date: 2022-08-13 11:35:43
-->

# [Codewars]-Codewars style ranking system___Charming__的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41882147/article/details/80984572?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058616781685360739%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058616781685360739&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-13-80984572-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_41882147/article/details/80984572?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058616781685360739%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058616781685360739&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-13-80984572-null-null.142^v40^control,185^v2^control&utm_term=codewars)

### Codewars风格的等级系统（Codewars style ranking system）

#### 题目：

*   写一个名叫`User`的类，用于计算用户的得分和等级。**（`User`类中必须包含`rank`和`progress`这两个属性，以及`incProgress()`这个方法）**
*   具体说明：

    *   等级从-8到8依次递增
    *   等级不包含0级，也就是说-1级的下一级是1
    *   用户可以完成一些习题，这些习题也是有难度等级的
    *   每次用户完成习题之后，就会根据习题难度（等级）重新计算用户的分数和等级
    *   积分一旦达到100就会升一级，然后积分减100
    *   一旦达到8级积分记为0，且不再有积分和等级的提高
    *   输入其他的等级应该抛出一个错误。
*   计分准则：

    *   完成同级题目获得3分
    *   完成比自己等级低1级的题目，获1分
    *   完成比自己等级低2级或更多的题目，不得分
    *   完成等级比自己高的题目，获`10 * d * d`（d为等级差）
*   举个栗子：

    *   等级**-8**的用户完成了等级为**-7**的题目，获得**10**分
    *   等级**-8**的用户完成了等级为**-6**的题目，获得40分
    *   依次类推…
    *   **特别注意的是，等级-1的用户完成了等级为1的题目，获得10分（因为没有0等级，所以等级跨度为1）**
*   测试用例

```
user.rank // => 用户等级初始为-8
user.progress // => 用户积分初始为0
user.incProgress(-7) // 表示用户挑战等级为-7的题目
user.progress // => 10 // 挑战成功获得10分
user.incProgress(-5) // will add 90 progress // 由于用户积分为10，不足以升级，所以当前等级依然为-8，于是挑战成功获得90分
user.progress # => 0 // progress is now zero // 10 + 90 = 100 , 于是用户等级提升，积分减少100 ，为0
user.rank # => -7 // rank was upgraded to -7 // 每增加100，等级增加1
```

#### 思路：

*   主要考察es6的类的用法
*   根据题目的意思来写代码应该没有很大的问题。
*   可能会给你造成麻烦的是：

    *   等级达到8之后积分应该清零
    *   -1到1的等级差为1
    *   输入大于8或小于-8或0，这些等级应该抛出错误
*   我用数组把等级储存起来，然后通过比较等级的下标（index）来计算积分

#### 解答：

```
class User {
  constructor() {
    this.rankArr = [-8,-7,-6,-5,-4,-3,-2,-1,1,2,3,4,5,6,7,8]
    this.pos = 0
    this.rank = this.rankArr[this.pos]
    this.progress = 0
  }

  incProgress(n) {
    let newPos = this.rankArr.indexOf(n)
    if (newPos === -1) {throw new Error()}
    let posSpan = newPos - this.pos;
    if (posSpan === 0) {
      this.progress += 3;
    } else if (posSpan  === -1) {
      this.progress += 1;
    } else if (posSpan > 0) {
      this.progress += posSpan * posSpan * 10;
    }
    let rankUp = Math.floor(this.progress/100)
    this.progress -= rankUp * 100
    this.pos += rankUp 
    this.rank = this.rankArr[this.pos]
    this.progress = this.rank === 8 ? 0 : this.progress;
  }
}
```