<!--yml
category: codewars
date: 2022-08-13 11:47:50
-->

# Codewars练习题目_翊木的博客-CSDN博客

> 来源：[https://blog.csdn.net/Xiaojia_guniang/article/details/108399940?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-108399940.nonecase](https://blog.csdn.net/Xiaojia_guniang/article/details/108399940?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-108399940.nonecase)

*   编写一个函数，它接受一个或多个单词组成的字符串，并返回相同的字符串，但将所有五个或五个以上字母单词颠倒(就像这个Kata的名称)。
*   传入的字符串将只由字母和空格组成。
*   只有当有一个以上的单词时，空格才会被包含。

```
package com.yimu.test;

@SuppressWarnings("all")
public class Test01 {
    public static String spinWords(String sentence) {

        String temp;
        String str;
        int j=0;
        StringBuilder stringBuilder = new StringBuilder();
        String[] s = sentence.split(" ");
        if(s.length>1){
            for (String s1 : s) {
                if(s1.length()>=5){
                    String[] s2 = s1.split("");
                    for (int i = 0; i < s2.length/2; i++) {
                        temp = s2[i];
                        s2[i] = s2[s2.length-1-i];
                        s2[s2.length-1-i]=temp;
                    }
                    for (String s3 : s2) {
                        stringBuilder.append(s3);
                    }
                    if(s.length==j+1){
                    }else{
                        stringBuilder.append(" ");
                    }
                }else if(s1.length()>0){
                    stringBuilder.append(s1);
                    if(s.length==j+1){
                    }else{
                        stringBuilder.append(" ");
                    }
                }
                j++;
            }
            str = stringBuilder.toString();
            return str;
        }else {
            if (sentence.length()>= 5) {
                String[] st = sentence.split("");
                for (int i = 0; i < st.length / 2; i++) {
                    temp = st[i];
                    st[i] = st[st.length - 1 - i];
                    st[st.length - 1 - i] = temp;
                }
                for (String s1 : st) {
                    stringBuilder.append(s1);
                }
                str=stringBuilder.toString();
                return str;
            }else{
                str=sentence;
                return str;
            }
        }
    }

    public static void main(String[] args) {
        String s = spinWords("This is a test");
        System.out.println(s);
    }
} 
```

*   给定一串单词，您需要找到得分最高的单词。
*   一个单词的每个字母都根据其在字母表中的位置对分数进行评分：a = 1, b = 2, c = 3等。
*   您需要将得分最高的单词作为字符串返回。
*   如果两个单词得分相同，则返回最早出现在原始字符串中的单词。
*   所有字母均为小写，所有输入均有效。

```
package com.yimu.test;

public class Test02 {
    public static String high(String s) {
        String str = "";
        int flag = 0;
        String[] s1 = s.split(" ");
        for (String s2 : s1) {
            String[] split = s2.split("");
            int i = 0;
            for (String word : split) {
                for (int j = 1; j < 27 ; j++) {
                    if (word.hashCode() == (96+j)) {
                        i+=j;
                    }
                }
            }
            if (i > flag) {
                flag = i;
                str = s2;
            }
        }
        return str;
    }

    public static void main(String[] args) {
        String s = high("");
        System.out.println(s);
    }
} 
```

*   ＃找到丢失的字母
*   编写一个方法，该方法将连续（递增）字母的数组作为输入，并返回数组中缺少的字母。
*   您将始终获得有效的数组。而且总是会丢失一个字母。数组的长度始终至少为2。
*   在一种情况下，数组始终包含字母。

```
package com.yimu.test;

public class Test03 {
    public static char findMissingLetter(char[] array){
        char ch = ' ';
        StringBuilder stringBuilder = new StringBuilder();
        for (char c : array) {
            stringBuilder.append(c);
        }
        String s = stringBuilder.toString();
        String[] split = s.split("");
        int i = split[0].hashCode();
        int j = 0;
        for (String s1 : split) {
            if (s1.hashCode() != i) {
                ch = (char) (j + 1);
                return ch;
            }
            i+=1;
            j = s1.hashCode();
        }
        return ch;
    }
    public static void main(String[] args) {
        char[] str = {'O','Q','R','S'};
        char c = findMissingLetter(str);
        System.out.println("结果"+c);
    }
} 
```

*   给定一个数字列表，请确定其元素的总和是奇数还是偶数。
*   将您的答案作为字符串匹配"odd"或"even"。
*   如果输入数组为空，则将其视为：（[0]具有零的数组）。

```
package com.yimu.test;

public class Test04 {
    public static String oddOrEven (int[] array) {
        int sum = 0;
        String str = null;
        if (array == null) {
            str="even";
        }
        for (int i : array) {
            sum+=i;
        }
        if (sum%2==0) {
            str="even";
        }else {
            str="odd";
        }
        return str;
    }

    public static void main(String[] args) {
        int[] ints = {};
        String s = oddOrEven(ints);
        System.out.println(s);

    }
} 
```

*   您的任务是创建一个函数，它可以接受任何非负整数作为参数，并将其数字按降序返回。从本质上说，就是重新排列这些数字，以产生可能的最大数字。

```
package com.yimu.test;

public class Test05 {
    public static int sortDesc(final int num) {
        String s = String.valueOf(num);
        String[] split = s.split("");
        int[] ints = new int[split.length];
        int i = 0;
        int temp = 0;
        for (String s1 : split) {
            ints[i] = Integer.parseInt(s1);
            i+=1;
        }
        for (int j = 0; j < ints.length; j++) {
            for (int k = 0; k < ints.length-j-1; k++) {
                if (ints[k]<ints[k+1]) {
                    temp=ints[k];
                    ints[k]=ints[k+1];
                    ints[k+1]=temp;
                }
            }
        }
        StringBuilder stringBuilder = new StringBuilder();
        for (int anInt : ints) {
            stringBuilder.append(anInt);
        }
        int i1 = Integer.parseInt(stringBuilder.toString());
        return i1;
    }

    public static void main(String[] args) {
        int i = sortDesc(1912345);
        System.out.println(i);
    }
} 
```