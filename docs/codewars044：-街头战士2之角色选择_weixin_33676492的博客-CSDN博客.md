<!--yml
category: codewars
date: 2022-08-13 11:46:47
-->

# codewars044: 街头战士2之角色选择_weixin_33676492的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_33676492/article/details/92001787?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-92001787.nonecase](https://blog.csdn.net/weixin_33676492/article/details/92001787?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-92001787.nonecase)

### Solution:

```
import java.util.*;
public class Solution{
  public static String[] streetFighterSelection(String[][] fighters, int[] position, String[] moves){

		Map<String, String> map = new HashMap<String, String>();
		for (int i = 0; i < 2; i++) {
			for (int j = 0; j < 6; j++) {
				if (i == 0) {
					map.put(String.format("%d,%d-up", i, j),
							String.format("%d%d%s", i, j, fighters[i][j]));
				} else {
					map.put(String.format("%d,%d-up", i, j), String.format(
							"%d%d%s", i - 1, j, fighters[i - 1][j]));
				}
				if (i == 1) {
					map.put(String.format("%d,%d-down", i, j),
							String.format("%d%d%s", i, j, fighters[i][j]));
				} else {
					map.put(String.format("%d,%d-down", i, j), String.format(
							"%d%d%s", i + 1, j, fighters[i + 1][j]));
				}
				if (j == 0) {
					map.put(String.format("%d,%d-left", i, j),
							String.format("%d%d%s", i, 5, fighters[i][5]));
				} else {
					map.put(String.format("%d,%d-left", i, j), String.format(
							"%d%d%s", i, j - 1, fighters[i][j - 1]));
				}
				if (j == 5) {
					map.put(String.format("%d,%d-right", i, j),
							String.format("%d%d%s", i, 0, fighters[i][0]));
				} else {
					map.put(String.format("%d,%d-right", i, j), String.format(
							"%d%d%s", i, j + 1, fighters[i][j + 1]));
				}
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

### Example Tests:

```
import org.junit.Test;
import static org.junit.Assert.assertEquals;
import org.junit.runners.JUnit4;
import java.util.*;

public class SolutionTest {  

    String[][] fighters = new String[][]{
              new String[] { "Ryu", "E.Honda", "Blanka", "Guile", "Balrog", "Vega" },
              new String[] { "Ken", "Chun Li", "Zangief", "Dhalsim", "Sagat", "M.Bison" },
    };

    @Test
    public void shouldWorkWithNoMoves() {
      String[] solution = new String[]{};
      assertEquals(solution, Solution.streetFighterSelection(fighters, new int[]{0,0}, new String[]{}));
    }

    @Test
    public void shouldWorkWithFewMoves(){
      String[] moves = new String[] { "up", "left", "right", "left", "left" };
      String[] solution = new String[] { "Ryu", "Vega", "Ryu", "Vega", "Balrog" };
      assertEquals(solution, Solution.streetFighterSelection(fighters, new int[] {0,0}, moves));
    }

    @Test
    public void shouldWorkWhenAlwaysMovingLeft(){
      String[] moves = new String[] { "left", "left", "left", "left", "left", "left", "left", "left" };
      String[] solution = new String[] { "Vega", "Balrog", "Guile", "Blanka", "E.Honda", "Ryu", "Vega", "Balrog" };
      assertEquals(solution, Solution.streetFighterSelection(fighters, new int[] {0,0}, moves));
    }

    @Test
    public void shouldWorkWhenAlwaysMovingRight(){
      String[] moves = new String[] { "right", "right", "right", "right", "right", "right", "right", "right" };
      String[] solution = new String[] { "E.Honda", "Blanka", "Guile", "Balrog", "Vega", "Ryu", "E.Honda", "Blanka" };
      assertEquals(solution, Solution.streetFighterSelection(fighters, new int[] {0,0}, moves));
    }

    @Test
    public void shouldUseAll4DirectionsClockwiseTwice(){
      String[] moves = new String[] { "up", "left", "down", "right", "up", "left", "down", "right" };
      String[] solution = new String[] { "Ryu", "Vega", "M.Bison", "Ken", "Ryu", "Vega", "M.Bison", "Ken" };
      assertEquals(solution, Solution.streetFighterSelection(fighters, new int[] {0,0}, moves));
    }

    @Test
    public void shouldWorkWhenAlwaysMovingDown(){
      String[] moves = new String[] { "down", "down", "down", "down" };
      String[] solution = new String[] { "Ken", "Ken", "Ken", "Ken" };
      assertEquals(solution, Solution.streetFighterSelection(fighters, new int[] {0,0}, moves));
    }

    @Test
    public void shouldWorkWhenAlwaysMovingUp(){
      String[] moves = new String[] { "up", "up", "up", "up" };
      String[] solution = new String[] { "Ryu", "Ryu", "Ryu", "Ryu" };
      assertEquals(solution, Solution.streetFighterSelection(fighters, new int[] {0,0}, moves));
    }    
} 
```