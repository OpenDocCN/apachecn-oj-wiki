<!--yml
category: codewars
date: 2022-08-13 11:45:37
-->

# codewars047: 街头霸王2_weixin_33881050的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_33881050/article/details/92001793?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-92001793.nonecase](https://blog.csdn.net/weixin_33881050/article/details/92001793?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-92001793.nonecase)

### Instructions

[Street Fighter 2](https://www.codewars.com/kata/street-fighter-2-character-selection-part-2/train/java)

### Solution:

```
package codewars.jan;

//--https://www.codewars.com/kata/5853213063adbd1b9b0000be/train/java
//--https://www.codewars.com/kata/street-fighter-2-character-selection-part-2/train/java
import java.util.*;

public class StreetFighter2 {
	private static String left(int i, int j, String[] arr) {
		int to = j;
		while (true) {
			to--;
			if (to == -1) {
				to = arr.length - 1;
			}
			if (!"".equals(arr[to])) {
				break;
			}
		}
		return String.format("%d%d%s", i, to, arr[to]);
	}

	private static String right(int i, int j, String[] arr) {
		int to = j;
		while (true) {
			to++;
			if (to == arr.length) {
				to = 0;
			}
			if (!"".equals(arr[to])) {
				break;
			}
		}
		return String.format("%d%d%s", i, to, arr[to]);
	}

	public static String[] superStreetFighterize(String[][] fighters,
			int[] position, String[] moves) {
		Map<String, String> map = new HashMap<String, String>();
		final int rows = fighters.length;
		final int cols = fighters[0].length;
		for (int i = 0; i < rows; i++) {
			for (int j = 0; j < cols; j++) {
				String fighter = fighters[i][j];
				if ("".equals(fighter)) {
					continue;
				}
				if (i == 0) {
					map.put(String.format("%d,%d-up", i, j),
							String.format("%d%d%s", i, j, fighters[i][j]));
				} else if ("".equals(fighters[i - 1][j])) {
					map.put(String.format("%d,%d-up", i, j),
							String.format("%d%d%s", i, j, fighters[i][j]));
				}

				else {
					map.put(String.format("%d,%d-up", i, j), String.format(
							"%d%d%s", i - 1, j, fighters[i - 1][j]));
				}
				if (i == rows - 1) {
					map.put(String.format("%d,%d-down", i, j),
							String.format("%d%d%s", i, j, fighters[i][j]));
				} else if ("".equals(fighters[i + 1][j])) {
					map.put(String.format("%d,%d-down", i, j),
							String.format("%d%d%s", i, j, fighters[i][j]));
				}

				else {
					map.put(String.format("%d,%d-down", i, j), String.format(
							"%d%d%s", i + 1, j, fighters[i + 1][j]));
				}

				map.put(String.format("%d,%d-left", i, j),
						left(i, j, fighters[i]));
				map.put(String.format("%d,%d-right", i, j),
						right(i, j, fighters[i]));

			}
		}
		List<String> list = new ArrayList<String>();
		String[] current = new String[] { String.valueOf(position[0]),
				String.valueOf(position[1]) };
		for (int i = 0; i < moves.length; i++) {
			String value = map.get(String.format("%s,%s-%s", current[0],
					current[1], moves[i]));
			list.add(value.substring(2));
			current[0] = String.valueOf(value.charAt(0));
			current[1] = String.valueOf(value.charAt(1));

		}
		return list.toArray(new String[0]);
	}
} 
```