<!--yml
category: codewars
date: 2022-08-13 11:47:48
-->

# java 落单,Codewars征战记录-JAVA篇_叫我叔叔就行的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_35740875/article/details/115783805?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-115783805.nonecase](https://blog.csdn.net/weixin_35740875/article/details/115783805?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-115783805.nonecase)

无意中发现一个代码题目的网站，做了一个题，深有感触。记下来大牛们的解决思路

渣渣程序员就是我了，我会先列自己的写法，再列大牛的写法，共勉。

题目：传入一个数字n，求3和5的倍数和。如果该数为3和5共同的倍数，则计算一次。

DEMO:传入数字10，求3和5的倍数和，所以需要计算3、5、6、9的和，即23

public int solution(intnumber) {int result = 0;for (int i = number - 1; i > 0; i--) {if (i%5 == 0 || i%3 == 0){

result= i +result;

}

}returnresult;

}

大神例子1，使用 intsteam

public int solution(intnumber) {return IntStream.range(3, number).filter(n -> n % 3 == 0 || n % 5 == 0).sum();

}

还有个不使用循环。。

/*The sum of multiples of 3 is 3 + 6 + 9 + ... = 3 (1+2+3+...)

The sum of mulitples of 5 is 5 + 10 + 15 + ... = 5 (1+2+3+...)

If we just sum these, we'll get double values when a number is divisble by both,

so we substract the sum of multiples of 15, which is obtained in a similar manner.

The upper bound cannot be floor function because the inputed number shouldn't count.*/

importjava.lang.Math;public classSolution {public int solution(intn) {int a = (int) Math.ceil(n/3d) - 1;int b = (int) Math.ceil(n/5d) - 1;int c = (int) Math.ceil(n/15d) - 1;return (3 * a * (a+1) + 5 * b * (b+1) - 15 * c * (c + 1)) / 2;

}

}

题目：ATM的密码只能有4或者6位的数字密码组成。写一个方法判断。

首推正则

public static booleanvalidatePin(String pin) {

// 自己正则写的不熟悉，用的是:[0-9]{4,4}|[0-9]{6,6}return pin.matches("\\d{4}|\\d{6}");

}

JDK8写法

public static booleanvalidatePin(String pin) {if(pin == null) return false;if (pin.length() == 4 || pin.length() == 6)returnpin.chars().allMatch(Character::isDigit);return false;

}

题目：将输入的字符串按照规定格式打印，输入的字符串范围A-Za-z

例如：ZpglnRxqenU，则输出 Z-Pp-Ggg-Llll-Nnnnn-Rrrrrr-Xxxxxxx-Qqqqqqqq-Eeeeeeeee-Nnnnnnnnnn-Uuuuuuuuuuu

用流应该是很快捷的，不过不熟悉，只能用笨方法了

public staticString accum(String s) {//your code

char[] chars =s.toUpperCase().toCharArray();

StringBuilder sb= newStringBuilder();

String tempStr= null;for(int i=0;i

sb.append(chars[i]);

tempStr=String.valueOf(chars[i]).toLowerCase();for(int j=0;j

 *sb.append(tempStr);

}

sb.append("-");

}

sb.delete(sb.length()-1,sb.length());returnsb.toString();

}

流写法

public staticString accum(String s) {return IntStream.range(0, s.length())

.mapToObj(i-> IntStream.range(0, i + 1)

.mapToObj(i1-> i1 == 0 ?String.valueOf(s.charAt(i)).toUpperCase() : String.valueOf(s.charAt(i)).toLowerCase())

.collect(Collectors.joining())

).collect(Collectors.joining("-"));

}

题目：简单来说就是一段话的首字母大写

源：How can mirrors be real if our eyes aren't real

转为：How Can Mirrors Be Real If Our Eyes Aren't Real

自己的是split然后拼接，就不上了，太丑陋=.=

importjava.lang.Character;public classJadenCase {publicString toJadenCase(String phrase) {if(phrase == null || phrase.equals("")) return null;char[] array =phrase.toCharArray();for(int x = 0; x < array.length; x++) {if(x == 0 || array[x-1] == ' ') {

array[x]=Character.toUpperCase(array[x]);

}

}return newString(array);

}

}

流写法

publicString toJadenCase(String phrase) {if (null == phrase || phrase.length() == 0) {return null;

}return Arrays.stream(phrase.split(" "))

.map(i-> i.substring(0, 1).toUpperCase() + i.substring(1, i.length()))

.collect(Collectors.joining(" "));

}

题目：找出奇怪的数字，即落单的数字

例如：20,1,-1,2,-2,3,3,5,5,1,2,4,20,4,-1,-2,5

找到5

我的思路是用Set，如果存在就将存在的移除，否则放入Set。然而，还是有简易写法。。

public static int findIt(int[] A) {int odd = 0;for (inti : A) {

odd^=i;

}returnodd;

}

一如既往也能用stream

public static int findIt(int[] arr) {return stream(arr).reduce(0, (x, y) -> x ^y);

}

题目：统计出现重复的字符的次数

例如：indivisibility   i出现了多次，所以返回1,因为只有一个i重复出现了。

我是先统一大写后，用了两个Set作过滤

public static intduplicateCount(String text) {

Set firstSet = new HashSet<>();

Set targetSet = new HashSet<>();for(Character c : text.toUpperCase().toCharArray()) {if(firstSet.contains(c)) {

targetSet.add(c);

}else{

firstSet.add(c);

}

}returntargetSet.size();

}

一行的流写法。。。

public static intduplicateCount(String text) {return (int)text.toLowerCase().chars().boxed().collect(Collectors.groupingBy(k->k,Collectors.counting())).values().stream().filter(e->e>1).count();

}

题目：给定几个单词，由中划线或者下划线连接，转为驼峰写法

toCamelCase("the-stealth-warrior"); // returns "theStealthWarrior"

toCamelCase("The_Stealth_Warrior"); // returns "TheStealthWarrior"

我是用apache的大小写转换，不过因为导包有点问题。

采用原始的split后，用StringBuilder拼接首字母大写的字符。

流的写法：

staticString toCamelCase(String s){

String[] words= s.split("[-_]+");returnArrays.stream(words)

.skip(1)

.map(w-> w.substring(0, 1).toUpperCase().concat(w.substring(1)))

.reduce(words[0], String::concat);

}

题目：验证信用卡题目

给一串正整数，如果个数为偶数则从第一个开始每隔1位作双倍处理

如果个数为奇数则从第二个开始每隔1位作双倍处理

如果双倍后大于9，则减去9.

1714 ==> [1*, 7, 1*, 4] ==> [2, 7, 2, 4]

12345 ==> [1, 2*, 3, 4*, 5] ==> [1, 4, 3, 8, 5]

891 ==> [8, 9*, 1] ==> [8, 18, 1]

最后将数字加在一起，如果能被10整除，则为正确。否则错误

思路:转成Integer集合，算出哪些需要双倍并处理的，最后sum一下。

public static booleanvalidate(String n){

List source = Arrays.stream(n.split("")).map(Integer::valueOf).collect(Collectors.toList());int index = source.size() % 2 == 0 ? 0:1;

Integer tempI= null;for(;index

tempI= source.get(index) * 2;

source.set(index,tempI>9?tempI-9:tempI);

}int result =source.stream().mapToInt(Integer::intValue).sum();return result % 10 == 0;

}

一如既往的流写法，这脑子真好使。。。

public static booleanvalidate(String n) {final boolean[] flag = {(n.length() & 1) == 1};returnArrays.stream(

n.split(""))

.map(Integer::parseInt)

.mapToInt(value->value)

.map(integer-> ((flag[0] ^= true) ? (integer * 2 - 1) % 9 + 1: integer))

.sum()% 10 == 0;

}

题目：投掷5次6面骰子，根据规则统计分数

Three 1's => 1000 points

Three 6's => 600 points

Three 5's => 500 points

Three 4's => 400 points

Three 3's => 300 points

Three 2's => 200 points

One 1 => 100 points

One 5 => 50 point

思路：先组合一下，然后根据规则计算对应的值

public classGreed{public static int greedy(int[] dice){

Map resultMap = Arrays.stream(dice).boxed().collect(Collectors.groupingBy(k->k,Collectors.counting()));

AtomicInteger point= newAtomicInteger();

resultMap.forEach((key,value)->{switch(key) {case 1:

point.getAndAdd(((value/3)*1000)+(value%3)*100);break;case 2:

point.getAndAdd(value- 3 >= 0 ? 200 : 0);break;case 3:

point.getAndAdd(value- 3 >= 0 ? 300 : 0);break;case 4:

point.getAndAdd(value- 3 >= 0 ? 400 : 0);break;case 5:

point.getAndAdd(((value/3)*500)+(value%3)*50);break;case 6:

point.getAndAdd(value- 3 >= 0 ? 600 : 0);break;default:break;

}

});returnpoint.intValue();

}

}

其实大道至简。。用流其实还搞复杂了点。

public static int greedy(int[] dice) {int n[] = new int[7];for (int d : dice) n[d]++;return n[1]/3*1000 + n[1]%3*100 + n[2]/3*200 + n[3]/3*300 + n[4]/3*400 + n[5]/3*500 + n[5]%3*50 + n[6]/3*600;

}*