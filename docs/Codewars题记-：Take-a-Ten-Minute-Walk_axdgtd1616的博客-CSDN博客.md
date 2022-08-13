<!--yml
category: codewars
date: 2022-08-13 11:42:04
-->

# Codewars题记 ：Take a Ten Minute Walk_axdgtd1616的博客-CSDN博客

> 来源：[https://blog.csdn.net/axdgtd1616/article/details/102313977?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-2-102313977-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/axdgtd1616/article/details/102313977?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059216781685328322%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059216781685328322&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-2-102313977-null-null.142^v40^control,185^v2^control&utm_term=codewars)

1、题目：

You live in the city of Cartesia where all roads are laid out in a perfect grid. You arrived ten minutes too early to an appointment, so you decided to take the opportunity to go for a short walk. The city provides its citizens with a Walk Generating App on their phones -- everytime you press the button it sends you an array of one-letter strings representing directions to walk (eg. ['n', 's', 'w', 'e']). You always walk only a single block in a direction and you know it takes you one minute to traverse one city block, so create a function that will return true if the walk the app gives you will take you exactly ten minutes (you don't want to be early or late!) and will, of course, return you to your starting point. Return false otherwise.

Note: you will always receive a valid array containing a random assortment of direction letters ('n', 's', 'e', or 'w' only). It will never give you an empty array (that's not a walk, that's standing still!).

2、我的解决方案

```
 1 class TenMinWalk { 2     public static boolean isValid(char[] walk) {
 3 
 4         if (walk.length!=10) {
 5             return false;
 6         }
 7         
 8         Map<Character, Integer> countMap = new HashMap<Character, Integer>();
 9         
10         countMap.put('n', 0); 11         countMap.put('s', 0); 12         countMap.put('w', 0); 13         countMap.put('e', 0); 14         
15         for (char c : walk) { 16             countMap.put(c, countMap.get(c)+1); 17 } 18         
19         return countMap.get('n').equals(countMap.get('s'))&&countMap.get('w').equals(countMap.get('e')); 20 } 21 }
```

3、最佳解决方案

```
 1 public class TenMinWalk { 2   public static boolean isValid(char[] walk) {
 3     if (walk.length != 10) {
 4       return false;
 5     }
 6     int x = 0, y = 0;
 7     for (int i = 0; i < 10; i++) {
 8       switch (walk[i]) { 9         case 'n': 10           y++; 11           break; 12         case 'e': 13           x++; 14           break; 15         case 's': 16           y--; 17           break; 18         case 'w': 19           x--; 20           break; 21 } 22 } 23     return x == 0 && y == 0; 24 } 25 }
```

4、总结

　　我的解决方案好奇葩啊，哈哈。

　　在最佳解决方案中，只新增了三个int变量，内存占用少。