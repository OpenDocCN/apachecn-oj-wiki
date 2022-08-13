<!--yml
category: codewars
date: 2022-08-13 11:52:01
-->

# codewars练习/Champernowne's Championship（钱珀瑙恩数计算第N位上的数字）_Soler_lia的博客-CSDN博客

> 来源：[https://blog.csdn.net/Soler_lia/article/details/79929831?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-79929831.nonecase](https://blog.csdn.net/Soler_lia/article/details/79929831?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-79929831.nonecase)

#### 原题： Ho ho! So you think you know integers, do you? Well then, young wizard, tell us what the Nth digit of the [Champernowne constant](https://en.wikipedia.org/wiki/Champernowne_constant) is! The constant proceeds like this: `0.12345678910111213141516...` I hope you see the pattern! Conjure a function that will accept an integer, `n`, and return the (one-indexed) `n`th digit of Champernowne's constant. Can you get it to run in constant time? For example: `n = 1` should return `0` (the very first digit) `n = 2` should return `1` (we ignore the period character since it's not a digit!) `n = 20` should return `4` (that's the `4` in the number `14`, 20th in sequence) For any invalid values, such as `0` and below, or non-integers, return... `NaN`! I hope (for your sake) that you've been practicing your mathemagical spells, because a naïve solution will not be fast enough to compete in this championship! Invoke with precision, and be wary of rounding errors in the realms of enormity! May the best integer win!      [aMoniker(the author)](http://https//www.codewars.com/users/aMoniker) 

这个简单的无限不循环小数定义为：把全体正整数从小到大依次写成一排，并在最前面加上小数点，得到的一个无限小数称为钱珀瑙恩常数。

```
0.12345678910111213...99100101102.....9991000100110021003100410051006.....9999
                                                        n(求第n位上的数)
```

分析钱珀瑙恩常数的特点，0~9是10个个位数占十位，10~99是90个数两位数占90*2位，100~999是900个三位数占900*3位，则i位数是9*10^（i-1）个占9*10^（i-1）*i位。先判断i的值，同时得出i位数组成的无理数有多少位，减去函数参数可得第n位数到最后差了多少位。最后可以用得出的数字算出n所指的数属于哪个数字。最后再获取到这个数字。

```
function champernowneDigit(n) {
  // it's only one integer; how hard can it be?
  if(!(Number.isInteger(n)&&n>0)) return NaN   // 如果n不是正整数，返回NaN
  let total = 10, i = 1;  //从个位数开始，通过循环计算出第n位是几位数，同时得出i位数的字符总个数
  while(total<n){ i++; total += 9*(10**(i-1))*(i)}
  let a = 10**i-1-Math.floor((total-n)/i)  求出第n位的i位整数
  a = a.toString();
  return parseInt(a[a.length-1-(total-n)%i])
}
```

```
贴一段其他人的代码
```

```
/**
 * Find the nth digit of the Champernowne constant (in base 10)
 * i.e. the string: "0.12345678910111213141516..."
 *
 * https://en.wikipedia.org/wiki/Champernowne_constant
 *
 * We consider digit number one to be the first zero before the decimal place,
 * and we do not count the decimal itself, since it is not a digit.
 *
 * @param  int n must be 1 or greater
 * @return int
 */
function champernowneDigit(n) {
  if (typeof n !== 'number' || n % 1 !== 0 || n <= 0) {
    return NaN;
  }

  let d = 0;     // digit count of the number at position n
  let count = 0; // total characters required for range of d digits
  let pivot = 0; // starting point of range of d digits

  // loop until we find the character count for the range of d digits
  do {
    d++;
    pivot = count;
    count += getNumChars(d);
  } while(n > count);

  // get the offset of the number from the pivot
  let offset = Math.ceil((n - pivot) / d);
  // get the number which the character falls within
  let number = offset + (d === 1 ? 0 : 10 ** (d - 1)) - 1;
  // get the index of the character within the number that we want
  let numOffset = n - (pivot + 1 + ((offset - 1) * d));
  return Number.parseInt(('' + number)[numOffset]);
}

/**
 * Get the number of characters that are needed
 * to represent the entire range of n-digit numbers.
 *
 * e.g. for 3-digit numbers, 2700 characters are needed
 *
 * Assumes base 10.
 *
 * @param  int n number of digits
 * @return int   number of characters needed
 */
function getNumChars(n) {
  let range = (10 ** n);
  if (n > 1) { range -= (10 ** (n - 1)); }
  return range * n;
}
```

```
champernowneDigit=Q=>{if(!Q||!Q.toFixed||Q<=0)return 0/0;for(Q-=2,C=B=1,N=9;C*N<Q;N*=10,B*=10,++C)Q-=N*C;return+(B+Math.floor(Q/C)+'')[Q%C]}
```