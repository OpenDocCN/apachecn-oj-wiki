<!--yml
category: codewars
date: 2022-08-13 11:42:23
-->

# JavaScript-codewars刷题_叶子不语的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_41804058/article/details/82682327?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-12-82682327-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/qq_41804058/article/details/82682327?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-12-82682327-null-null.142^v40^control,185^v2^control&utm_term=codewars)

```
题目意:一个电影院售票员在没有本金的情况下,进行售票,如果能够用收到的钱进行找零,则交易成功,如果整个队伍都能交易成功,返回YES,
否则,返回NO.根据介绍,创建一个判断该排队队伍能不能成功交易.
Sample:
 tickets([25, 25, 50]) // => YES
 tickets([25, 100]) // => NO.
 tickets([25, 25, 50, 50, 100]) // => NO. 

我的解决方案:
```

```
function tickets(peopleInLine) {
    var twentyFifth = [], fifty = [], hundred = [],flag='';
    for(var j=0;j<peopleInLine.length;j++){
        //给的钱不是25
        if(peopleInLine[j]!=25){
            //给了50
            if(peopleInLine[j]==50){
                //判断前面有没有钱可以找零
               if(twentyFifth.length>0){
                   //可以找零,则减去找零的,顺便将刚收的50收起来
                   twentyFifth.shift();
                   fifty.push(50);
                   flag= 'YES';
               }else{
                   flag= 'NO';
                   break;
               }
            }//给了100
            else if(peopleInLine[j]==100){
                //能不能找零成功
                if(twentyFifth.length>0 && fifty.length>0){
                    twentyFifth.shift();
                    fifty.shift();
                    hundred.push(100);
                    flag = 'YES';
                }
                else if(twentyFifth.length>=3){
                    twentyFifth.splice(0,3);//会改变原数组,返回删除的数所组成的数组
                    hundred.push(100);
                    flag = 'YES';
                } else{
                    flag= 'NO';
                    break;
                }
            }
        }else{
            twentyFifth.push(25);
            flag = 'YES';
        }
    }
    return flag;
}
```

codewars的最优答案:

```
function Clerk(name) {
    this.name = name;
    this.money = {
        25 : 0,
        50 : 0,
        100: 0
    };
    this.sell = function(element, index, array) {
        this.money[element]++;

        switch (element) {
            case 25:
                return true;
            case 50:
                this.money[25]--;
                break;
            case 100:
                this.money[50] ? this.money[50]-- : this.money[25] -= 2;
                this.money[25]--;
                break;
        }
        return this.money[25] >= 0;
    };
}

function tickets(peopleInLine){
    var vasya = new Clerk("Vasya");
    return peopleInLine.every(vasya.sell.bind(vasya)) ? "YES" : "NO";
}
```

自己编程过程中出现的问题

- 问题一:开始队列中某一个人能成功找零,直接return 'yes',程序不会判断后面的数据,直接返回yes了,导致程序出错.

- 问题二:问题二:忘记3个25元也能给100找零这一种情况.

- 问题三:只要出现不能找零的情况,就应该退出循环,直接return no'.