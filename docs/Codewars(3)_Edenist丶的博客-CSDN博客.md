<!--yml
category: codewars
date: 2022-08-13 11:27:19
-->

# Codewars(3)_Edenist丶的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_36624415/article/details/86296709?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-86296709.142^v40^control,185^v2^control](https://blog.csdn.net/qq_36624415/article/details/86296709?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-86296709.142^v40^control,185^v2^control)

前一阵子在codewars上做了一道题，觉得很不错，期间也踩了很多很多坑，在此把我做题的整个过程和牵扯到的知识点做一个汇总，以及我在思考过程中犯的一些错误，希望看完之后能对你有帮助，不要犯我犯的错误，想些这篇已经很久了，一直没有时间。废话不多说，上题！
Input

**a string strng of n positive numbers (n = 0 or n >= 2)
Let us call weight of a number the sum of its digits. For example 99 will have “weight” 18, 100 will have “weight” 1.
Two numbers are “close” if the difference of their weights is small.
Task:
For each number in strng calculate its “weight” and then find two numbers of strng that have:
the smallest difference of weights ie that are the closest
with the smallest weights
and with the smallest indices (or ranks, numbered from 0) in strng
Output:
an array of two arrays, each subarray in the following format:
[number-weight, index in strng of the corresponding number, original corresponding number instrng]
or a pair of two subarrays (Haskell, Clojure, FSharp) or an array of tuples (Elixir, C++)
or a (char*) in C mimicking an array of two subarrays
or a matrix in R (2 rows, 3 columns, no columns names)
The two subarrays are sorted in ascending order by their number weights if these weights are different, by their indexes in the string if they have the same weights.
Examples:
Let us call that function closest**
****strng = “103 123 4444 99 2000”
the weights are 4, 6, 16, 18, 2 (ie 2, 4, 6, 16, 18)
closest should return [[2, 4, 2000], [4, 0, 103]] (or ([2, 4, 2000], [4, 0, 103])
or [{2, 4, 2000}, {4, 0, 103}] or … depending on the language)
because 2000 and 103 have for weight 2 and 4, ther indexes in strng are 4 and 0.
The smallest difference is 2.
4 (for 103) and 6 (for 123) have a difference of 2 too but they are not
the smallest ones with a difference of 2 between their weights.
…
strng = “80 71 62 53”
All the weights are 8.
closest should return [[8, 0, 80], [8, 1, 71]]
71 and 62 have also:**

*   the smallest weights (which is 8 for all)
*   the smallest difference of weights (which is 0 for all pairs)
*   but not the smallest indices in strng.
    …
    strng = “444 2000 445 544”
    the weights are 12, 2, 13, 13 (ie 2, 12, 13, 13)
    closest should return [[13, 2, 445], [13, 3, 544]] or ([13, 2, 445], [13, 3, 544])
    or [{13, 2, 445}, {13, 3, 544}] or …
    444 and 2000 have the smallest weights (12 and 2) but not the smallest difference of weights;
    they are not the closest.
    Here the smallest difference is 0 and in the result the indexes are in ascending order.
    …
    closest(“444 2000 445 644 2001 1002”) --> [[3, 4, 2001], [3, 5, 1002]] or ([3, 4, 2001],
    [3, 5, 1002]]) or [{3, 4, 2001}, {3, 5, 1002}] or …
    Here the smallest difference is 0 and in the result the indexes are in ascending order.
    …
    closest(“239382 162 254765 182 485944 468751 49780 108 54”)
    The weights are: 27, 9, 29, 11, 34, 31, 28, 9, 9.
    closest should return [[9, 1, 162], [9, 7, 108]] or ([9, 1, 162], [9, 7, 108])
    or [{9, 1, 162}, {9, 7, 108}] or …
    108 and 54 have the smallest difference of weights too, they also have
    the smallest weights but they don’t have the smallest ranks in the original string.
    …
    closest(“54 239382 162 254765 182 485944 468751 49780 108”)
    closest should return [[9, 0, 54], [9, 2, 162]] or ([9, 0, 54], [9, 2, 162])
    or [{9, 0, 54}, {9, 2, 162}] or …**

**If n == 0, `closest("") should return [] or ([], []) in Haskell, Clojure, FSharp or [{}, {}] in Elixir or {{0,0,0},{0,0,0}} in C++, “[{}, {}]” in Go, “{{0,0,0},{0,0,0}}” in C, NULL in R.
See Example tests for the format of the results in your language.**
这是给定的函数：
char* closest(char* strng) {
// your code
}
在这个函数体里写你的方法。
嗯，题目是很长，开始我本来想跳过的，但是学习就是不断的自虐，不然怎么能够进步！
简而言之，就是给一个字符串，这个字符串由一串数字组成，其中数字之间以空格" "隔开，然后需要计算每个数字的weight，**最后将最小的并且是相差最小的两个数字的weight包括其在字符串中是第几个以及它本身是多少合并成一个特定的格式进行输出（这一点我开始并没有注意到，我用自己的方法得到了结果但一直无法通过）** **如果有一样的weight那么必须返回字符串中位置靠前的两个。** 确实挺坑的当时觉得，后来确实让我学到了不少。好了下面来讲一下我的思路，如果你有更好的思路那么请一定要贴出来。

下面，踩坑现场来了：
1、看完这道题之后，我以为他要我仅仅返回一个二维数组（并没有注意到返回的是一个char型指针）。
那么好了，一维数组返回是很简单，申请内存就OK，但是二维数组怎么返回呢？这里我想当然的用一维数组的方式去声明一个二维数组，像这样：int (*arr)[2][3]=…结果发现其实这样是错的，其中的原因较为复杂，简单来说可以看下面：

为了让C语言函数返回一个二维数组，有些人这样定义函数：
int **foo(int rows, int columns)
然后在函数中费劲心机拼出来一个这样的malloc语句：
int (*result)[columns] = (int (*)[columns])malloc(rows * columns * sizeof(int));
在函数内读写这个数组发现很正常，等把数组返回给调用函数后，再读写这个数组就crash掉了。
原因其实很简单，函数返回值类型是int **foo，而实际返回值类型是int (*bar)[columns]，它们的区别就是foo[1] - foo[0] = sizeof(int *)，而bar[1] - bar[0] = sizeof(int [columns])。把bar赋值给foo以后，访问foo[1][0]会访问到啥呢？首先要看foo[1]是个啥，foo[1] = *(foo + 1)，那个1虽然看起来是1，但是实际加到foo上的大小实际上是foo指向元素的大小，如果说sizeof(int) = sizeof(int *) = 4的话，也就是foo值增加4，然后对这个地址取值，放到bar中取到了啥呢，实际上取出来的是bar[0][1]，所以说，实际上foo[1] = bar[0][1]，然而bar[0][1]并不是一个指针或者数组，所以读foo[1][0]就会crash掉。
正确的做法是这样的：

int **result = (int **)malloc(rows * sizeof(int *));
for (int i = 0; i < columns; i++)
{
result[i] = (int *)malloc(columns * sizeof(int));
}
好了，简单介绍完了之后那么我们就可以利用这个二维数组来返回了（并没有注意函数类型）。”解决“了这个问题之后，我就想，既然要计算weight，那么我们就来先计算输入字符串中每个数字串的weight吧，当时感觉好像也不是很难，就创建一个数组，然后把每个数字串的weight保存进去，然后再找最小的两个呗，然而我错了，之后返回的类型中有数字串的下标和原本的数字串，如果单单一遍计算weight的话之后还要重新回到字符串进行比对，这样问题就会很复杂，这个题目给的数字串也很刁钻，如果有一样的话我如何知道我找的这两个最小的到底是那两个。这样明显是行不通的。而且我考虑到为了节省空间，我不想直接声明一个数组，这样它的长度被固定了可能造成空间的浪费。那么先来计算总共多少个数字串需要进行比对吧。

```
 char *p = strng;
   int number = 1;                   
   while(*p)
   {
       if((*p++)==' ') number++;
   } 
```

这样用指针就可以声明一个大小刚刚好的数组了，那么我们具体要多大的数组呢，考虑到效率的问题，我只想要遍历这个字符串一次，那么我就必须把题目要求的信息全部存起来，那么总共多少个呢，是的，number*3个元素，同时你也明白为什么我这里要声明一个char *p，因为之后要移动strng了，当然处于安全性，你可以在声明一个来保护strng，当然这里无可厚非了。我们用int型指针数组来处理这一段，需要把数字串转为int，C语言中转换还是比较难受的，总的来说这种转换不算难。这一段总体的代码如下：

```
 char *p = strng;
   int number = 1;                   
   int arrflag = 0;
   int putInToArrFlag = 0;
   long long strToNum = 0;
   int numberWeight = 0;
   while(*p)
   {
       if((*p++)==' ') number++;
   }
   long *arr = (long *)malloc(sizeof(long)*number*3);
   while(*strng)
   {
       if(*strng!=' ')
       {
           strToNum = strToNum*10 + (*strng-'0');
           numberWeight = numberWeight + (*strng-'0');
           *strng++;
       }
       else
       {
           arr[putInToArrFlag++] = numberWeight;
           arr[putInToArrFlag++] = arrflag++;
           arr[putInToArrFlag++] = strToNum;
           strToNum = 0;
           numberWeight = 0;
           *strng++;
       }
   }
   arr[putInToArrFlag++]=numberWeight;
   arr[putInToArrFlag++]=arrflag;
   arr[putInToArrFlag] = strToNum; 
```

当然，你可以处理逻辑把这段代码改写的更好，注意这最后3行是个我踩的最后一个坑，调试程序时才发现的，写程序还是不能太急躁。
好了，这里我们得到了一个arr数组，那么下来就找呗，简单！然而我又想错了，此时的问题简化为，如何在一个数组中找到最小并且相差最小的两个数字并且要找出这两个数字下标还有这两个数字本身，同时还要注意一些刁难你的数字。好吧，条件是有点多，那么一步一步来吧，最开始我想直接找，直接用一个循环只找arr数组中0 ，3， 6，…的两个数字差值最小的两个数，接着把他们放进二维数组呗，然而并不能，会有很多很多的偶然性，能被刁难住！不论我怎么样去处理这个逻辑都不行。难道我得再用一个一维数组把这些weight找出来再排序再到arr中找？这也太脑残了吧！果断放弃。最后觉得还是直接排arr靠谱，但是只排序0,3,6…这些，仅仅把其后的下标和原数字跟着调换就行了，诶呀我去，这一通给我整的。代码如下

```
int temp1,temp2,temp3;
   for(int i=0;i<number*3-3;i=i+3)
   {
       for(int j=0;j<number*3-3-i;j+=3)
       {
           if(arr[j]>arr[j+3])
           {
               temp1 = arr[j+3];
               arr[j+3] = arr[j];
               arr[j] = temp1;
               temp2 = arr[j+3+1];
               arr[j+3+1] = arr[j+1];
               arr[j+1] = temp2;
               temp3 = arr[j+3+2];
               arr[j+3+2] = arr[j+2];
               arr[j+2] = temp3;
           }
       }
   } 
```

接下来找最小的那不好找了，也没有任何逻辑上可能出错的可能了，笨点是笨点，那就找！

```
int mindif = abs(arr[3]-arr[0]);
   int flag = 0;
   int flag2 = 3;

   for(int i=0;i<number*3;i+=3)
   {
       for(int j=i+3; j<number*3;j+=3)
       {
           if(mindif>abs(arr[i]-arr[j]))
           {
               mindif = abs(arr[i]-arr[j]);
               flag = i;
               flag2 = j;
           }
       }
   } 
```

好，现在已经找到了，来给二维数组赋值！

```
 for(int i=0;i<2;i++)
   {
       if(i==0)
       {
           for(int j=0;j<3;j++)
           {
               arrToReturn[i][j]=arr[flag++];
           }
       }
       else
       {
           for(int j=0;j<3;j++)
           {
               arrToReturn[i][j]=arr[flag2++];
           }
       }
   } 
```

return 结束！？结束了吗？显然不可能，虽然数字都找出来了，但是返回啥呢，此时我才注意到要返回的是char * 也就是一个字符串，需要和答案进行比对的字符串！我返回二维数组是干啥呢？
这里先给出题目作者的主函数是怎么写的

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <criterion/criterion.h>

char* array2D2StringInt(int a[][3], int row, int col);
char** split(char *str, const char *delim, int *length);
int nbWeight(const char* str);
int compare2DArray(const void * pa, const void * pb);
char* closest(char* strng);

void dotest(char* s, char *expr) {
    char *sact = closest(s);
    if(strcmp(sact, expr) != 0)
        printf("Error. Expected \n%s\n but got \n%s\n", expr, sact);
    cr_assert_str_eq(sact, expr, "");
    free(sact); sact = NULL;
}

Test(closest, ShouldPassAllTheTestsProvided) {

    dotest("", "{{0,0,0},{0,0,0}}");
    dotest("456899 50 11992 176 272293 163 389128 96 290193 85 52", "{{13, 9, 85}, {14, 3, 176}}");
    dotest("239382 162 254765 182 485944 134 468751 62 49780 108 54", "{{8, 5, 134}, {8, 7, 62}}");
    dotest("241259 154 155206 194 180502 147 300751 200 406683 37 57", "{{10, 1, 154}, {10, 9, 37}}");
    dotest("89998 187 126159 175 338292 89 39962 145 394230 167 1", "{{13, 3, 175}, {14, 9, 167}}");
    dotest("462835 148 467467 128 183193 139 220167 116 263183 41 52", "{{13, 1, 148}, {13, 5, 139}}");

    dotest("403749 18 278325 97 304194 119 58359 165 144403 128 38", "{{11, 5, 119}, {11, 9, 128}}");
    dotest("28706 196 419018 130 49183 124 421208 174 404307 60 24", "{{6, 9, 60}, {6, 10, 24}}");
    dotest("189437 110 263080 175 55764 13 257647 53 486111 27 66", "{{8, 7, 53}, {9, 9, 27}}");
    dotest("79257 160 44641 146 386224 147 313622 117 259947 155 58", "{{11, 3, 146}, {11, 9, 155}}");
    dotest("315411 165 53195 87 318638 107 416122 121 375312 193 59", "{{15, 0, 315411}, {15, 3, 87}}");
} 
```

我去，这跟我之前写的十几道题都不一样啊，第一次看到返回要求这么花里胡哨的，那么咋办呢？
我想到了strcpy和strcat这两个函数，还有就是把数字转换为字符串并且符合ascii码要求的sprintf函数（此时我并没有意识到sprintf函数有多么强大，虽然不像C#和java那样直接写就完事儿了，但对于比较原始的C来说还是惊讶到我了）那么我就开始拼这个字符串，后来发现怎么都不对，怎么都得不到结果，什么strcpy strcat呀各种用，各种逻辑处理得到一个返回的字符串，后来发现转化数字的sprintf会把之前拼的东西全部覆盖了，当时觉得真坑，这可咋办啊，有没有好办法？ 查！
结果还真有，来好好介绍一下sprintf函数：

在将各种类型的数据构造成字符串时，sprintf 的强大功能很少会让你失望。由于sprintf 跟printf 在用法上几乎一样，只是打印的目的地不同而已，前者打印到字符串中，后者则直接在命令行上输出。这也导致sprintf 比printf 有用得多。

sprintf 是个变参函数，定义如下：
int sprintf( char *buffer, const char *format [, argument] … );
除了前两个参数类型固定外，后面可以接任意多个参数。而它的精华，显然就在第二个参数：
格式化字符串上。

printf 和sprintf 都使用格式化字符串来指定串的格式，在格式串内部使用一些以“%”开头的格式说明符（format specifications）来占据一个位置，在后边的变参列表中提供相应的变量，最终函数就会用相应位置的变量来替代那个说明符，产生一个调用者想要 的字符串。

格式化数字字符串
sprintf 最常见的应用之一莫过于把整数打印到字符串中，所以，spritnf 在大多数场合可以替代
itoa。

如：
//把整数123 打印成一个字符串保存在s 中。
sprintf(s, “%d”, 123); //产生"123"
可以指定宽度，不足的左边补空格：
sprintf(s, “%8d%8d”, 123, 4567); //产生：" 123 4567"
当然也可以左对齐：
sprintf(s, “%-8d%8d”, 123, 4567); //产生：“123 4567”
也可以按照16 进制打印：
sprintf(s, “%8x”, 4567); //小写16 进制，宽度占8 个位置，右对齐
sprintf(s, “%-8X”, 4568); //大写16 进制，宽度占8 个位置，左对齐

这样，一个整数的16 进制字符串就很容易得到，但我们在打印16 进制内容时，通常想要一种左边补0 的等宽格式，那该怎么做呢？很简单，在表示宽度的数字前面加个0 就可以了。
sprintf(s, “%08X”, 4567); //产生：“000011D7”
上面以”%d”进行的10 进制打印同样也可以使用这种左边补0 的方式。

这里要注意一个符号扩展的问题：比如，假如我们想打印短整数（short）-1 的内存16 进制表示形式，在Win32 平台上，一个short 型占2 个字节，所以我们自然希望用4 个16 进制数字来打印它：
short si = -1;
sprintf(s, “%04X”, si);
产 生“FFFFFFFF”，怎么回事？因为spritnf 是个变参函数，除了前面两个参数之外，后面的参数都不是类型安全的，函数更没有办法仅仅通过一个“%X”就能得知当初函数调用前参数压栈时被压进来的到底 是个4 字节的整数还是个2 字节的短整数，所以采取了统一4 字节的处理方式，导致参数压栈时做了符号扩展，扩展成了32 位的整数-1，打印时4 个位置不够了，就把32 位整数-1 的8 位16 进制都打印出来了。

如果你想看si 的本来面目，那么就应该让编译器做0 扩展而不是符号扩展（扩展时二进制左边补0 而不是补符号位）：
sprintf(s, “%04X”, (unsigned short)si);
就可以了。或者：
unsigned short si = -1;
sprintf(s, “%04X”, si);

sprintf 和printf 还可以按8 进制打印整数字符串，使用”%o”。注意8 进制和16 进制都不会打
印出负数，都是无符号的，实际上也就是变量的内部编码的直接的16 进制或8 进制表示。

控制浮点数打印格式
浮点数的打印和格式控制是sprintf 的又一大常用功能，浮点数使用格式符”%f”控制，默认保
留小数点后6 位数字，比如：
sprintf(s, “%f”, 3.1415926); //产生"3.141593"
但有时我们希望自己控制打印的宽度和小数位数，这时就应该使用：”%[m.nf](http://m.nf)”格式，其中m 表
示打印的宽度，n 表示小数点后的位数。比如：
sprintf(s, “%10.3f”, 3.1415626); //产生：" 3.142"
sprintf(s, “%-10.3f”, 3.1415626); //产生："3.142 "
sprintf(s, “%.3f”, 3.1415626); //不指定总宽度，产生：“3.142”

注意一个问题，你猜
int i = 100;
sprintf(s, “%.2f”, i);
会打出什么东东来？“100.00”？对吗？自己试试就知道了，同时也试试下面这个：
sprintf(s, “%.2f”, (double)i);
第 一个打出来的肯定不是正确结果，原因跟前面提到的一样，参数压栈时调用者并不知道跟i相对应的格式控制符是个”%f”。而函数执行时函数本身则并不知道当 年被压入栈里的是个整数，于是可怜的保存整数i 的那4 个字节就被不由分说地强行作为浮点数格式来解释了，整个乱套了。不过，如果有人有兴趣使用手工编码一个浮点数，那么倒可以使用这种方法来检验一下你手工编 排的结果是否正确。

字符/Ascii 码对照
我们知道，在C/C++语言中，char 也是一种普通的scalable 类型，除了字长之外，它与short，
int，long 这些类型没有本质区别，只不过被大家习惯用来表示字符和字符串而已。（或许当年该把
这 个类型叫做“byte”，然后现在就可以根据实际情况，使用byte 或short 来把char 通过typedef 定义出来，这样更合适些）于是，使用”%d”或者”%x”打印一个字符，便能得出它的10 进制或16 进制的ASCII 码；反过来，使用”%c”打印一个整数，便可以看到它所对应的ASCII 字符。以下程序段把所有可见字符的ASCII 码对照表打印到屏幕上（这里采用printf，注意”#”与”%X”合用时自动为16 进制数增加”0X”前缀）：
for(int i = 32; i < 127; i++) {
printf("[ %c ]: %3d 0x%#04X/n", i, i, i);
}

连接字符串
sprintf 的格式控制串中既然可以插入各种东西，并最终把它们“连成一串”，自然也就能够连
接字符串，从而在许多场合可以替代strcat，但sprintf 能够一次连接多个字符串（自然也可以同时
在它们中间插入别的内容，总之非常灵活）。比如：
char* who = “I”;
char* whom = “CSDN”;
sprintf(s, “%s love %s.”, who, whom); //产生：“I love CSDN. "
strcat 只能连接字符串（一段以’’结尾的字符数组或叫做字符缓冲，null-terminated-string），但有时我们有两段字符缓冲区，他们并不是以 ’’结尾。比如许多从第三方库函数中返回的字符数组，从硬件或者网络传输中读进来的字符流，它们未必每一段字符序列后面都有个相应的’’来结尾。如果直接 连接，不管是sprintf 还是strcat 肯定会导致非法内存操作，而strncat 也至少要求第一个参数是个null-terminated-string，那该怎么办呢？我们自然会想起前面介绍打印整数和浮点数时可以指定宽度，字符串 也一样的。比如：
char a1[] = {‘A’, ‘B’, ‘C’, ‘D’, ‘E’, ‘F’, ‘G’};
char a2[] = {‘H’, ‘I’, ‘J’, ‘K’, ‘L’, ‘M’, ‘N’};
如果：
sprintf(s, “%s%s”, a1, a2); //Don’t do that!
十有八九要出问题了。是否可以改成：
sprintf(s, “%7s%7s”, a1, a2);
也没好到哪儿去，正确的应该是：
sprintf(s, “%.7s%.7s”, a1, a2);//产生：“ABCDEFGHIJKLMN”
这 可以类比打印浮点数的”%[m.nf](http://m.nf)”，在”%m.ns”中，m 表示占用宽度（字符串长度不足时补空格，超出了则按照实际宽度打印），n 才表示从相应的字符串中最多取用的字符数。通常在打印字符串时m 没什么大用，还是点号后面的n 用的多。自然，也可以前后都只取部分字符：
sprintf(s, “%.6s%.5s”, a1, a2);//产生：“ABCDEFHIJKL”
在 许多时候，我们或许还希望这些格式控制符中用以指定长度信息的数字是动态的，而不是静态指定的，因为许多时候，程序要到运行时才会清楚到底需要取字符数组 中的几个字符，这种动态的宽度/精度设置功能在sprintf 的实现中也被考虑到了，sprintf 采用”*”来占用一个本来需要一个指定宽度或精度的常数数字的位置，同样，而实际的宽度或精度就可以和其它被打印的变量一样被提供出来，于是，上面的例子 可以变成：
sprintf(s, “%.*s%.*s”, 7, a1, 7, a2);
或者：
sprintf(s, “%.*s%.*s", sizeof(a1), a1, sizeof(a2), a2);
实际上，前面介绍的打印字符、整数、浮点数等都可以动态指定那些常量值，比如：
sprintf(s, “%-*d", 4, ‘A’); //产生"65 "
sprintf(s, "%#0*X”, 8, 128); //产生"0X000080"，"#"产生0X
sprintf(s, "%*.*f”, 10, 2, 3.1415926); //产生” 3.14"

打印地址信息
有时调试程序时，我们可能想查看某些变量或者成员的地址，由于地址或者指针也不过是个32 位的数，你完全可以使用打印无符号整数的”%u”把他们打印出来：
sprintf(s, “%u”, &i);
不过通常人们还是喜欢使用16 进制而不是10 进制来显示一个地址：
sprintf(s, “%08X”, &i);
然而，这些都是间接的方法，对于地址打印，sprintf 提供了专门的”%p”：
sprintf(s, “%p”, &i);
我觉得它实际上就相当于：
sprintf(s, “%0*x”, 2 * sizeof(void *), &i);
利用sprintf 的返回值
较少有人注意printf/sprintf 函数的返回值，但有时它却是有用的，spritnf 返回了本次函数调用
最终打印到字符缓冲区中的字符数目。也就是说每当一次sprinf 调用结束以后，你无须再调用一次
strlen 便已经知道了结果字符串的长度。如：
int len = sprintf(s, “%d”, i);
对于正整数来说，len 便等于整数i 的10 进制位数。
下面的是个完整的例子，产生10 个[0, 100)之间的随机数，并将他们打印到一个字符数组s 中，
以逗号分隔开。

```
#include
#include
#include
int main() {
srand(time(0));
char s[64];
int offset = 0;
for(int i = 0; i < 10; i++) {
offset += sprintf(s + offset, "%d,", rand() % 100);
}
s[offset - 1] = '/n';
printf(s);
return 0;
} 
```

设想当你从数据库中取出一条记录，然后希望把他们的各个字段按照某种规则连接成一个字
符串时，就可以使用这种方法，从理论上讲，他应该比不断的strcat 效率高，因为strcat 每次调用
都需要先找到最后的那个’’的位置，而在上面给出的例子中，我们每次都利用sprintf 返回值把这
个位置直接记下来了。

使用sprintf 的常见问题
sprintf 是个变参函数，使用时经常出问题，而且只要出问题通常就是能导致程序崩溃的内存访
问错误，但好在由sprintf 误用导致的问题虽然严重，却很容易找出，无非就是那么几种情况，通
常用眼睛再把出错的代码多看几眼就看出来了。
参考自：[https://blog.csdn.net/glorin/article/details/6538412](https://blog.csdn.net/glorin/article/details/6538412)

既然了解了sprintf，那么来照猫画虎写出

```
sprintf(strToReturn,"{{%d,%d,%d},{%d,%d,%d}}",arrToReturn[0][0],arrToReturn[0][1],arrToReturn[0][2],arrToReturn[1][0],arrToReturn[1][1],arrToReturn[1][2]); 
```

这样也不是什么难事了。OK 编译通过，成功晋升到6kyu。开心！
这里贴出完整的代码，我看到这个问题好像没有多少非常高赞的答案，暂时先不贴了。这里贴出我的整个代码

```
char* closest(char* strng) {
   int **arrToReturn = (int **)malloc(sizeof(int *)*2);              
   char *strToReturn;
   strToReturn = (char*)malloc(sizeof(char)*26);
   for(int i=0;i<3;i++)
   {
       arrToReturn[i] = (int *)malloc(sizeof(int)*3);
   }
   if(*strng=='\0')
   {
       for(int i=0;i<2;i++)
       {
           for(int j=0;j<3;j++)
           {
               arrToReturn[i][j] = 0;
           }
       }
       sprintf(strToReturn,"{{%d,%d,%d},{%d,%d,%d}}",arrToReturn[0][0],arrToReturn[0][1],arrToReturn[0][2],arrToReturn[1][0],arrToReturn[1][1],arrToReturn[1][2]);
       return strToReturn;
   }
   char *p = strng;
   int number = 1;                   
   int arrflag = 0;
   int putInToArrFlag = 0;
   long long strToNum = 0;
   int numberWeight = 0;
   while(*p)
   {
       if((*p++)==' ') number++;
   }
   int *arr = (int *)malloc(sizeof(int)*number*3);
   while(*strng)
   {
       if(*strng!=' ')
       {
           strToNum = strToNum*10 + (*strng-'0');
           numberWeight = numberWeight + (*strng-'0');
           *strng++;
       }
       else
       {
           arr[putInToArrFlag++] = numberWeight;
           arr[putInToArrFlag++] = arrflag++;
           arr[putInToArrFlag++] = strToNum;
           strToNum = 0;
           numberWeight = 0;
           *strng++;
       }
   }
   arr[putInToArrFlag++]=numberWeight;
   arr[putInToArrFlag++]=arrflag;
   arr[putInToArrFlag] = strToNum;
   int flag = 0;
   int flag2 = 3;
   int temp1,temp2,temp3;
   for(int i=0;i<number*3-3;i=i+3)
   {
       for(int j=0;j<number*3-3-i;j+=3)
       {
           if(arr[j]>arr[j+3])
           {
               temp1 = arr[j+3];
               arr[j+3] = arr[j];
               arr[j] = temp1;
               temp2 = arr[j+3+1];
               arr[j+3+1] = arr[j+1];
               arr[j+1] = temp2;
               temp3 = arr[j+3+2];
               arr[j+3+2] = arr[j+2];
               arr[j+2] = temp3;
           }
       }
   }
   int mindif = abs(arr[3]-arr[0]);
   for(int i=0;i<number*3;i+=3)
   {
       for(int j=i+3; j<number*3;j+=3)
       {
           if(mindif>abs(arr[i]-arr[j]))
           {
               mindif = abs(arr[i]-arr[j]);
               flag = i;
               flag2 = j;
           }
       }
   }
   for(int i=0;i<2;i++)
   {
       if(i==0)
       {
           for(int j=0;j<3;j++)
           {
               arrToReturn[i][j]=arr[flag++];
           }
       }
       else
       {
           for(int j=0;j<3;j++)
           {
               arrToReturn[i][j]=arr[flag2++];
           }
       }
   }
   sprintf(strToReturn,"{{%d, %d, %d}, {%d, %d, %d}}",arrToReturn[0][0],arrToReturn[0][1],arrToReturn[0][2],arrToReturn[1][0],arrToReturn[1][1],arrToReturn[1][2]);
   return strToReturn;
} 
```

其实还有个办法，就是用结构体，这个问题就被化简的非常简单了。结构体的方法大家可以自己研究研究！
说实话，做完之后觉得提升真的挺大，前路还漫长，继续走下去，希望我能够考上名古屋大学，给大家分享更多的知识互相交流！

如果你有更好的方法，请一定要分享出来。让我们之后看到的人得到提升！