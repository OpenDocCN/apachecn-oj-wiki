<!--yml
category: codewars
date: 2022-08-13 11:26:06
-->

# JavaScript学习 CodeWars 打怪升级日记 你最少需要准备几把伞_Cinderella_hou的博客-CSDN博客

> 来源：[https://blog.csdn.net/Cinderella_hou/article/details/82812404?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036032516782184646989%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=166036032516782184646989&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-5-82812404-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/Cinderella_hou/article/details/82812404?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036032516782184646989%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=166036032516782184646989&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-5-82812404-null-null.142^v40^control,185^v2^control&utm_term=codewars)

CodeWars 是一个在线编程网站，其奖励机制像打怪升级。你不能查看高于你级别的问题的答案。除非自己通过提交测试。通过提交之后可以看到各种解法排行榜 。通过对比自己解法和排行榜对比，可以找到差距，提高能力。

# 题目意思：

[题目地址](https://www.codewars.com/kata/a-man-and-his-umbrellas/javascript)
我简单的翻译: 一个人每天从家去公司，如果早晨下雨就从家带把伞到公司，如果下午不下雨就不把伞带回家。 如果早晨不下雨，则不带伞去公司，但是下午下雨会从公司带伞回家。 输入为 一个数组值为未来几天的天气预报，一天两次，分别为早上和下午的天气预报。只有"rainy" 和 "thunderstorms" 需要下雨，其他天气不需要。 计算出 为了保证不淋雨至少需要几把伞。
函数名为： minUmbrellas
e.g.
minUmbrellas(["rainy", "clear", "rainy", "cloudy"])
// should return 2
// Because on the first morning, he needs an umbrella to take, and he leaves it at work.
// So on the second morning, he needs a second umbrella.

# 我的解法

```
function isRainy(w) {
	if(w === 'rainy'|| w === 'thunderstorms') {
		return true;
	}
	return false;
}

function isHome(day) {
  if(day % 2 === 0) {
    return true; 
  }
  return false;
}
function minUmbrellas(weather) {
  // TODO
  let s = 0,
    h = 0, 
    w = 0,
    ha = [],
    wa = [];
    weather.forEach( (item, index) => {

      if(isRainy(item)) {
        if(isHome(index)) {
          h = h - 1;
          w = w + 1;
        } else {
          w = w -1;
          h = h + 1;
        }
        ha.push(h);
        wa.push(w);
      }
    })

    let min = 0;
    ha.forEach( un => {
      if(un < min)  {
        min = un;
      }
    });
    let minW = 0;
    wa.forEach( un => {
    	if( un < minW) {
    		minW = un;
    	}
    })
    return -min - minW;
} 
```

# codewars最佳实践

```
function minUmbrellas(w) {
  var rain="rainy,thunderstorms",home=0,office=0
  for(var i=0;i<w.length;i+=2){
    if(rainingAtMorning()){
      if(noUmbrellaInHome()) buyAnUmbrellaAtHome()
      takeUmbrellaToOffice()
      if(rainingAtAfternoon()) takeUmbrellaToHome()
    }
    else if(rainingAtAfternoon()) {
      if(noUmbrellaInOffice()) buyAnUmbrellaAtOffice()
      takeUmbrellaToHome()
    }
  }
  return home+office

  function rainingAtMorning(){return rain.includes(w[i])}
  function rainingAtAfternoon(){return rain.includes(w[i+1]+"")}
  function noUmbrellaInHome(){return home==0}
  function noUmbrellaInOffice(){return office==0}
  function buyAnUmbrellaAtHome(){home++}
  function buyAnUmbrellaAtOffice(){office++}
  function takeUmbrellaToOffice(){home--;office++}
  function takeUmbrellaToHome(){home++;office--}
} 
```

# 几个测试用例

有几个测试用例，看到这道题目的同学自己试一下吧
minUmbrellas(["sunny", "windy", "sunny", "clear"])
// should return 0
// Because it doesn't rain at all

minUmbrellas(["rainy", "rainy", "rainy", "rainy", "thunderstorms", "rainy"])
// should return 1