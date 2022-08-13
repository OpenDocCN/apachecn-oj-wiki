<!--yml
category: codewars
date: 2022-08-13 11:33:39
-->

# [codewars][Java] 翻译摩斯码_尉迟海棠的博客-CSDN博客

> 来源：[https://blog.csdn.net/GYK0812/article/details/95342784?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-95342784.142^v40^control,185^v2^control](https://blog.csdn.net/GYK0812/article/details/95342784?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-95342784.142^v40^control,185^v2^control)

> In this kata you have to write a simple [Morse code](https://en.wikipedia.org/wiki/Morse_code) decoder. While the Morse code is now mostly superceded by voice and digital data communication channels, it still has its use in some applications around the world.
> 
> The Morse code encodes every character as a sequence of "dots" and "dashes". For example, the letter `A` is coded as `·−`, letter `Q` is coded as `−−·−`, and digit `1` is coded as `·−−−−`. The Morse code is case-insensitive, traditionally capital letters are used. When the message is written in Morse code, a single space is used to separate the character codes and 3 spaces are used to separate words. For example, the message `HEY JUDE` in Morse code is `···· · −·−−   ·−−− ··− −·· ·`.
> 
> **NOTE:** Extra spaces before or after the code have no meaning and should be ignored.
> 
> In addition to letters, digits and some punctuation, there are some special service codes, the most notorious of those is the international distress signal [SOS](https://en.wikipedia.org/wiki/SOS) (that was first issued by [Titanic](https://en.wikipedia.org/wiki/RMS_Titanic)), that is coded as `···−−−···`. These special codes are treated as single special characters, and usually are transmitted as separate words.
> 
> Your task is to implement a function that would take the morse code as input and return a decoded human-readable string.
> 
> For example:
> 
> ```
> MorseCodeDecoder.decode(".... . -.--   .--- ..- -.. .")
> //should return "HEY JUDE"
> ```

我的code：

```
import java.util.ArrayList;

public class MorseCodeDecoder {
    public static String decode(String morseCode) {
        // your brilliant code here, remember that you can access the preloaded Morse code table through MorseCode.get(code)
    	 String[] list = morseCode.split(" ");   //用空格分隔，并存入一个数组中
		 ArrayList<String> arr = new ArrayList<>();
		 int space = 0;
         int count =0;
		 String s = "";

		for(int i =0 ; i<list.length ; i++)
		 {
			 arr.add(MorseCode.get(list[i]));
		 }
		for(int k=0; k<arr.size(); k++)
		{

			if(arr.get(k) == null)
			{
				space ++;

			}
			else    //第k个元素不等于null
			{
				if(space ==0)
				{
					s += arr.get(k);
					count++;
				}
				else
				{
					if(count ==0)    //前面的元素为空
					{
						s += arr.get(k);
						space = 0;
						count ++;
					}
					else
					{
						s += " "+arr.get(k);
						space = 0;	
					}
				}

			}

		}

		 return s;
	 }

}

分几种情况进行讨论：
1\. 链表中元素 = null
   1> 将 space ++；， 并且不做任何输出
2\. 链表中元素非空
   1> space = 0， 说明当前元素之前没有null元素，可以直接输出；如 [E,null,null,E]
      s = s+ arr.get(k);
   2> space >0, 说明当前元素前为null, 此时需要判断null元素是出现在链表开头，如： 
      [null,null,E,null,null,E]; 还是中间位置,如： [E,null,null,E]
      ~ 如果null出现在开头，如[null,null,E,null,null,E],则标志变量count=0；
      ~ 如果null出现在中间，如[E,null,null,E]， 则标志变量count =1; 
```

Clever code：

```
public class MorseCodeDecoder {
    public static String decode(String morseCode) {
      String result = "";
      for(String word : morseCode.trim().split("   ")) {
        for(String letter : word.split("\\s+")) {
          result += MorseCode.get(letter);
        }
        result += ' ';
      }
      return result.trim();
    }
}

// .trim() 方法用于删除字符串两端的字符
// "\\s+" 为正则表达式，"\"为转义字符，"\s+" 代表多个空白字符，可以是空格，回车，换行，换页，制表符等。这个正则表达式经常用到
```