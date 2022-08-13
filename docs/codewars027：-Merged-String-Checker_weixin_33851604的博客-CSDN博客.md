<!--yml
category: codewars
date: 2022-08-13 11:52:06
-->

# codewars027: Merged String Checker_weixin_33851604的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_33851604/article/details/92001761?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-92001761.nonecase](https://blog.csdn.net/weixin_33851604/article/details/92001761?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-92001761.nonecase)

5 kyu

[https://www.codewars.com/kata/54c9fcad28ec4c6e680011aa/train/java](https://www.codewars.com/kata/54c9fcad28ec4c6e680011aa/train/java)

```
package codewars;

//--https://www.codewars.com/kata/54c9fcad28ec4c6e680011aa/train/java
public class StringMerger {
	public static boolean isMerge(String s, String part1, String part2) {
		if (s.length() != part1.length() + part2.length()) {
			return false;
		}
		StringBuilder t = new StringBuilder(s);
		StringBuilder sb1 = new StringBuilder(part1);
		StringBuilder sb2 = new StringBuilder(part2);
		while (t.length() > 0) {
			int len1 = 0;
			int len2 = 0;

			for (int i = 0; i < sb1.length(); i++) {

				if (t.charAt(i) == sb1.charAt(i)) {
					len1++;
				} else {
					break;
				}
			}
			for (int i = 0; i < sb2.length(); i++) {

				if (t.charAt(i) == sb2.charAt(i)) {
					len2++;
				} else {
					break;
				}
			}
			if (len1 == 0 && len2 == 0) {
				return false;
			}
			if (len1 > len2) {
				sb1.delete(0, 1);
				t.delete(0, 1);

			} else {
				sb2.delete(0, 1);
				t.delete(0, 1);
			}

		}
		if (t.length() == 0 && sb1.length() == 0 && sb2.length() == 0) {
			return true;
		} else {
			return false;
		}

	}
} 
```

```
package codewars;
import org.junit.Test;
import static org.junit.Assert.*;

public class StringMergerTest {

  @Test
  public void normalHappyFlow() {
    assertTrue("codewars can be created from code and wars", StringMerger.isMerge("codewars", "code", "wars"));
    assertTrue("codewars can be created from cdwr and oeas", StringMerger.isMerge("codewars", "cdwr", "oeas"));
    assertTrue("Going bananas!", StringMerger.isMerge("bananas", "a", "banans"));
    assertTrue("Going bananas!", StringMerger.isMerge("bananas", "a", "bannas"));
    assertTrue("Going bananas!", StringMerger.isMerge("bananas", "baaa", "nns"));
    assertTrue("p4,?`?G.&gt;j' is a merge of 'p?G.&gt;j' and '4,?`", StringMerger.isMerge("p4,?`?G.&gt;j", "p?G.&gt;j", "4,?`"));
    assertTrue("'Can we merge it? Yes, we can!' is a merge of 'Ca eerg t es, w c!' and 'nw mei?Yean' ", StringMerger.isMerge("Can we merge it? Yes, we can!", "Ca eerg t es, w c!", "nw mei?Yean"));

    assertFalse("Codewars are not codwars", StringMerger.isMerge("codewars", "cod", "wars"));
    assertFalse("Going bananas!", StringMerger.isMerge("bananas", "a", "abnans"));
    assertFalse("Going bananas!", StringMerger.isMerge("bananas", "a", "banasn"));

  }

}
```