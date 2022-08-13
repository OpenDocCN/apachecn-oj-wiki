<!--yml
category: codewars
date: 2022-08-13 11:51:26
-->

# [Codewars]-Gap in Primes___Charming__的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41882147/article/details/79657619?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-79657619.nonecase](https://blog.csdn.net/qq_41882147/article/details/79657619?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-79657619.nonecase)

## Gap in Primes

#### 题目：

*   [Gap in Primes题目](https://www.codewars.com/kata/561e9c843a2ef5a40c0000a4/train/javascript)
*   简单说一下题目，在给定的整数m,n之间，找出所有间隔为g的素数对，而且这个素数对之间没有其他素数，返回小的那个素数对。`gap(g,m,n)`
*   举个例子：

    *   `gap(2,2,50)`
    *   2和50之间，间隔为2的素数对有`3-5, 5-7, 11-13, 17-19, 29-31, 41-43`，应该返回`[3,5]`。
    *   如果找不到则返回null

    #### 思路：

    *   1.从m到n循环
    *   2.找到素数并储存起来记为`temp`
    *   3.继续找下一个素数`k`，如果`k`和`temp`的差距为`g`，则返回`[temp,k]`，否则继续执行第2、3步

#### 判断素数的思路：

*   判断素数的范围只需要在 （2，2–√） （ 2 ， 2 ） 之间即可
*   为什么是 2–√ 2 ？

    *   是否是素数是用比它小的数去除它看能否出尽来判断的，而如果能出尽的话那么除数是成对存在的，比如22=2*11，2和11就是一对，而这一对只要判断一个就可以了，因此这种除数判断的下界为2，而上界为被除数开根号。 

#### 解答：

```
function gap(g, m, n) {

    var result = null;
    var temp = []
    for(var k = m ; k <= n ; k++){
        if( isPrimeNumber(k) ){
            if(temp.length >= 1){
                if( k - temp[0] == g){
                    result = [temp[0],k]
                    break
                }else{
                    temp[0] = k
                }
            }else{
                temp.push(k)
            }

        }
    }

    function isPrimeNumber(num){
        for(var i = 2 ; i*i <= num ; i ++){
            if( num%i==0){
                return false
                break
            }
        }
        return true
    }
    return result
}
```