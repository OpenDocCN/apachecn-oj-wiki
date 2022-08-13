<!--yml
category: codewars
date: 2022-08-13 11:52:02
-->

# [js] codewars 练习_aefg95955的博客-CSDN博客

> 来源：[https://blog.csdn.net/aefg95955/article/details/101449087?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-101449087.nonecase](https://blog.csdn.net/aefg95955/article/details/101449087?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-101449087.nonecase)

//增加方法
String.prototype.myNewMethod = function(){
　　return this.toUpperCase();
} ;
"abc".myNewMethod();

//匹配成对的括号
function isBalanced(string){
  var count = 0;
  for(var i = 0; i < string.length; i++) {
    if (string[i] === '(') count ++;
    if (string[i] === ')') count --;
    if (count < 0) return false;
  }

  return count === 0;
}

//数组从小到大系统排序
#1
    var array = [8,4,6,2,7,9,3,5,74,5];
    var systemSort = function(array) {
        return array.sort(function(a, b) {
            return a - b;
        });
    }
    systemSort(array);
    console.log(array);

#2
    function isBalanced(s){
      s = s.replace(/[^()]+/g, '');
      var m = /\(\)/, r = /\(\)/g;      
      while(m.test(s)) {          
       s = s.replace(r, '');    
      }                
      return s === '';
    }

//一串数字，选出相邻4个数乘积最小的排列

    function LowestProduct(input) {
        if (input.length < 4)
            return 'Number is too small';
        var numbers = input.split('').map(Number);
        //这个map加可以把数组元素都变成number格式，但是不加好像也没什么影响
        var product = i => numbers[i] * numbers[i + 1] * numbers[i + 2] * numbers[i + 3];
        //箭头函数，相当于
        //var product = function(i){
        //    return numbers[i] * numbers[i + 1] * numbers[i + 2] * numbers[i + 3];
        //};
        var lowest = product(0);
        for (var i = 1; i <= numbers.length - 4; i++) {
            var test = product(i);
            lowest = Math.min(lowest, test);
        }
        return lowest;
    }

//过滤数组中字符串长度等于4的元素

#1

     const friend = friends => friends.filter(friend => friend.length === 4);

#2

    function friend(friends) {
        var output = [];
        friends.map(function(friend) {
            if (friend.length === 4) {
                output.push(friend);
            }
        });
        return output;
    }

#3

    function friend(friends) {
        var a = [];
        if (Array.isArray(friends)) {
            for (var k in friends) {
                var i = friends[k];
                if (typeof i === "string") {
                    if (i.length === 4) {
                        a.push(i)
                    }
                }
            }
        }
        return a;
    }

//tug_o_war 。 很蠢的一个小游戏

function tug_o_war(teams) {
    function sum(arr) {
        return arr.reduce(function(s, e) {
            return s + e
        });
    }
    var res,
        s1 = sum(teams[0]),
        s2 = sum(teams[1]);
    if (s1 === s2) {
        res = teams[0][0] === teams[1][4] ? 0 : teams[0][0] > teams[1][4] ? 1 : 2;
    } else res = s1 > s2 ? 1 : 2;
    return ["It's a tie!", "Team 1 wins!", "Team 2 wins!"][res];
}