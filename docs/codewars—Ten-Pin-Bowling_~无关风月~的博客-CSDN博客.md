<!--yml
category: codewars
date: 2022-08-13 11:50:38
-->

# codewars—Ten-Pin Bowling_~无关风月~的博客-CSDN博客

> 来源：[https://blog.csdn.net/zxm1306192988/article/details/72808838?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-72808838.nonecase](https://blog.csdn.net/zxm1306192988/article/details/72808838?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-72808838.nonecase)

OJ地址：[https://www.codewars.com/kata/ten-pin-bowling/train/java](https://www.codewars.com/kata/ten-pin-bowling/train/java)

试题的大致意思：

投10局保龄球，每局的目标是把10个保龄球都投中
前9局，每局最多能投两个球，如果第一投就10个全中（用‘X’表示），就不用投第二个。

每局投球会出现两种情况：
**Strikes投**
用‘X’表示
表示本局的第一投就10球全中。该局的得分是10+后两个投球的得分。
如果有两局的投球情况是 X 54 那么得分就是（10+5+4）+5+4=28

**Spares投**
用‘/’表示
表示一局中的第二投把10个球都投中了。该局投球得分是10+下一次投球的得分。
如果有两局的投球情况是 9/ 54 那么得分就是 （10+5）+5+4=24

正因为有上面的规定，所以第10局比较特殊。最多可以投3个球。
因为如果第10局第一个球投了 ‘X’ 那么需要加上后两次投球的得分。
如果第10局第二个投球全中了即 ‘/’ 那么需要加上后一次投球的得分。
当然后补的最后一次投球本身分数不算。
后补的两个或一次投球是全新的10个保龄球。

```
 @Test
    public void BasicTests() {

        assertEquals(20, Solution.bowling_score("11 11 11 11 11 11 11 11 11 11"));

        assertEquals(300, Solution.bowling_score("X X X X X X X X X XXX"));

        assertEquals(171, Solution.bowling_score("X X 9/ 80 X X 90 8/ 7/ 44"));

        assertEquals(110, Solution.bowling_score("1/ 1/ 1/ 1/ 1/ 1/ 1/ 1/ 1/ 1/1"));

        assertEquals(20, Solution.bowling_score("11 11 11 11 11 11 11 11 11 11"));

        assertEquals(20, Solution.bowling_score("00 00 00 00 00 00 00 00 00 XX0"));

        assertEquals(20, Solution.bowling_score("00 00 00 00 00 00 00 00 00 1/X"));
    }
```

解法一：
按正常扫描每一个字符，每局按只有一个‘X’字符或者有两个字符进行处理，最后特殊处理最后一个字符。
需要保持两个变量，flag1和flag2 来记录后面要加的投球次数，由于每次投球除了本身的分数外，还可能受到前面的‘X’或‘/’影响，所以最多另外加两次，加完后相应的flag–。当再此遇到需要记录后面投球的‘X’或者‘/’时，将已经减为0的flag赋值。由于flag最打会等于2，所以两个变量足够了。

```
class Solution {
    public static int bowling_score(String frames) {
        String[] a = frames.split(" ");
        int sum = 0;
        int flag1 = 0;
        int flag2 = 0;
        for (int i = 0; i < 10; i++) {
            if (a[i].length() == 1) {
                sum = sum + 10;
                if (flag1 > 0) {
                    sum = sum + 10;
                    flag1--;
                }
                if (flag2 > 0) {
                    sum = sum + 10;
                    flag2--;
                }
                if (flag1 == 0) {
                    flag1 = 2;
                } else {
                    flag2 = 2;
                }
            } else {
                char x = a[i].charAt(0);
                int xshu = 0;
                if (x == 'X') {
                    sum = sum + 10;
                    if (flag1 > 0) {
                        sum = sum + 10;
                        flag1--;
                    }
                    if (flag2 > 0) {
                        sum = sum + 10;
                        flag2--;
                    }
                    if (flag1 == 0) {
                        flag1 = 2;
                    } else {
                        flag2 = 2;
                    }
                } else {
                    xshu = Integer.parseInt(x + "");
                    sum = sum + xshu;
                    if (flag1 > 0) {
                        sum = sum + xshu;
                        flag1--;
                    }
                    if (flag2 > 0) {
                        sum = sum + xshu;
                        flag2--;
                    }
                }
                char y = a[i].charAt(1);
                if (y == '/') {
                    sum = sum + 10 - xshu;
                    if (flag1 > 0) {
                        sum = sum + 10 - xshu;
                        flag1--;
                    }
                    if (flag2 > 0) {
                        sum = sum + 10 - xshu;
                        flag2--;
                    }
                    if (flag1 == 0) {
                        flag1 = 1;
                    } else {
                        flag2 = 1;
                    }
                } else if (y == 'X') {
                    if (i != 9) {
                        sum = sum + 10;
                    }
                    if (flag1 > 0) {
                        sum = sum + 10;
                        flag1--;
                    }
                    if (flag2 > 0) {
                        sum = sum + 10;
                        flag2--;
                    }
                } else {
                    sum = sum + Integer.parseInt(String.valueOf(y));
                    if (flag1 > 0) {
                        sum = sum + Integer.parseInt(String.valueOf(y));
                        flag1--;
                    }
                    if (flag2 > 0) {
                        sum = sum + Integer.parseInt(String.valueOf(y));
                        flag2--;
                    }
                }

            }
        }
        if (a[9].length() == 3) {
            char last = a[9].charAt(2);
            if (last == 'X') {
                if (flag1 > 0) {
                    sum = sum + 10;
                    flag1--;
                }
                if (flag2 > 0) {
                    sum = sum + 10;
                    flag2--;
                }
            } else {
                int lastN = Integer.parseInt(last + "");
                if (flag1 > 0) {
                    sum = sum + lastN;
                    flag1--;
                }
                if (flag2 > 0) {
                    sum = sum + lastN;
                    flag2--;
                }
            }

        }

        return sum;
    }
}
```

解法二（较好）：
平等的看待每次投球
先用一个整形数组记录每次投球本身的得分。
然后遍历10局，如果遇到‘X’或‘/’直接累加后面相应投球次数的得分，累加每局的实际得分。

```
public class Solution {
    public static int bowling_score(String frames) {
        return new BowlingGame(frames).getScore();
    }
}

class BowlingGame {
    private int[] rolls;

    BowlingGame(String frames) {
        String[] strRolls = frames.replaceAll(" ", "").split("");
        rolls = new int[strRolls.length];
        for (int i = 0; i < strRolls.length; i++) {
            try {
                rolls[i] = Integer.valueOf(strRolls[i]);
            } catch (NumberFormatException e) {
                if (strRolls[i].equals("/")) {
                    rolls[i] = 10 - rolls[i - 1];
                } else {
                    rolls[i] = 10;
                }
            }
        }
    }

    int getScore() {
        int frame = 0;
        int score = 0;
        for (int i = 0; i < 10; i++) {
            if (rolls[frame] == 10) {
                score += 10 + rolls[frame + 1] + rolls[frame + 2];
                frame++;
            } else if (rolls[frame] + rolls[frame + 1] == 10) {
                score += 10 + rolls[frame + 2];
                frame += 2;
            } else {
                score += rolls[frame] + rolls[frame + 1];
                frame += 2;
            }
        }
        return score;
    }
}
```

方法三：

```
import java.util.*;
import java.util.stream.Collectors;

public class Solution {

    public static int bowling_score(String frames) {
        String[] fArr = frames.split(" ");
        int score = 0;

        for (int i = 0 ; i < fArr.length ; i++) {
            if (fArr[i].matches("X|[0-9]/")) {
                if (i < 9) fArr[i] = Arrays.stream(fArr, i, fArr.length)
                                           .collect(Collectors.joining(""))
                                           .substring(0, 3);
            }
            score += fArr[i].replaceAll("[0-9]/","X")
                            .chars()
                            .map( n -> !Character.isDigit((char) n) ? 10 : Integer.valueOf(Character.toString((char) n)))
                            .sum();
        }
        return score;
    }
}
```

the idea is:

*   split the frame string in String[] fArr
*   initiate the score
*   run through fArr

    *   if the current frame is a strike or a spare, you need to check further in order to be able to add the extra points to the score, so:

        *   if you’re not working with the last frame (whose index is 9), you join the next frames (this is the first “stream” part of the code) and you keep only the 3 first characters of what you obtain (the beauty of the thing is that it works what ever the next frames are!) and you add this string to the current “cell” of fArr (this way, you have in this cell the current frame, and all that you need for the extra points)
    *   at this point, you calculate the number of points gained for the current frame (knowing already the extra points coming from the next frames in case of spare or strike). To do that (second “stream” part, that is disguised behind the chars() method):

        *   you replace spares (meaning, one digit and the / after) by a X (this way you’ll have only digits and X characters in the current string. See below)
        *   you make a stream of the thing (chars()), one element of the stream being this time 1 character of the initial “current frame string”
        *   you transform each element/character into an int. There lays the utility of the conversion of spares that was made upper: if the charcter is a digit, take the equivalent int, but if it’s not a digit, it’s a X, so you know it’s a 10 value.
        *   sum the result
        *   add the sum to the score thing
*   end of the job!

From：[https://www.codewars.com/kata/5531abe4855bcc8d1f00004c/solutions/java](https://www.codewars.com/kata/5531abe4855bcc8d1f00004c/solutions/java)