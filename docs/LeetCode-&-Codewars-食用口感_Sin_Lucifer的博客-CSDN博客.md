<!--yml
category: codewars
date: 2022-08-13 11:38:21
-->

# LeetCode & Codewars 食用口感_Sin_Lucifer的博客-CSDN博客

> 来源：[https://blog.csdn.net/puqdgood/article/details/53437263?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-25-53437263-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/puqdgood/article/details/53437263?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058816781685396932%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058816781685396932&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-25-53437263-null-null.142^v40^control,185^v2^control&utm_term=codewars)

**引言**

为了提高自己的编程水平以及代码能力，前些日子开始每天去完成一两道LeetCode与CodeWars的题目，用了下来感觉两者不同之处在于CodeWars：一是界面更炫酷些，二则是比起LeetCode，它更偏向于一种对语言的使用，在提升算法能力的同时加强自身选择的某种语言的能力。

而LeetCode则是纯算法题，更考验个人的算法能力，目前为止就做过一些Easy的题目和Medium的题目。最蠢的解法总是很快就能想到，提交之后虽然Accept了，但是看着自己的解法的运行耗时比别人慢了一大截总是十分难受。于是乎我基本上都会再去用另一种方法去再解决一遍，强制自己提升自己的水平。

* * *

下面做下归纳：

# **LeetCode：**

## 1\. Two Sum

*   Difficulty: Easy
*   Description：

    Given an array of integers, return indices of the two numbers such that they add up to a specific target.

    You may assume that each input would have exactly one solution.

    Example:
    Given nums = [2, 7, 11, 15], target = 9,

    Because nums[0] + nums[1] = 2 + 7 = 9,

    return [0, 1].

题目不难，给出一个数组，并给出一个数，求数组中哪两个数之和正好为给出的数，最后返回下标。

最开始的想法，冒泡匹配呗

```
public class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer,Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length - 1; i++) {
            map.put(target - nums[i],i);

            if (map.get(nums[i+1]) != null){
                return new int[]{map.get(nums[i+1]),i+1};
            }
        }

        return null;
    }
}
```

虽然AC了，但是耗时37ms，且时间复杂度为O（n^2）

于是了解到我们可以使用一些特殊的数据结构来优化我们的算法——HashMap

哈希是通过一个特定的函数将要存储的数据存放到计算得到的位置，因此哈希的搜索的时间复杂度为O（1），利用这一点，我们可以写出下述答案

```
public class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer,Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length - 1; i++) {
            map.put(target - nums[i],i);

            if (map.get(nums[i+1]) != null){
                return new int[]{map.get(nums[i+1]),i+1};
            }
        }

        return null;
    }
}
```

由于只使用了一次循环，所以时间复杂度是O（n），具体做法是将 `target - num[i]` 放进HashMap中当作Key，而Value则是num[i]的下标i，当下次遍历的时候发现我们需要的答案在HashMap里面，直接就可以将i弹出，然后将当前i和map中的i作为答案返回。

曾考虑过先对数组进行排序后用target/2作为判断依据去找值，但因为返回的是下标，且题目给的下标是固定的，所以该想法不能实施。

## 2\. Add Two Numbers

*   Difficulty: Medium
*   Description：

    You are given two linked lists representing two non-negative numbers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

    Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
    Output: 7 -> 0 -> 8

题目考查了链表相加，这实际上是在做大数相加的处理，至于逆序则是为了对齐其单位以方便进行操作，故处理思路即先取值相加，当一方链表无法再相加之时，直接将另一条链表合并到当前链表中，另一个比较重要的问题是要处理进位问题，我的处理方法是对位加的时候即时处理进位，即保留个位，将下一个节点的基础值+1，每次计算的时候计算新建链表值与两条链表值之和。

由于存在链表合并，故合并时候的进位也需要考虑，我采取了设置标记位，在整体处理完后再处理一遍标记位，该算法的时间复杂度为O（1）

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
       ListNode result = new ListNode(0);
        ListNode temp = result;
        int tempInt;
        boolean flag = false;
        while (l1 != null || l2 != null) {
            if (l1 == null) {
                temp.val = temp.val + l2.val;
                flag = true;
                temp.next = l2.next;
                break;
            }
            if (l2 == null) {
                temp.val = temp.val + l1.val;
                flag = true;
                temp.next = l1.next;
                break;
            }

            tempInt = temp.val + l1.val + l2.val;

            if (tempInt >= 10) {
                temp.val = tempInt % 10;
                temp.next = new ListNode(1);
            } else {
                temp.val = tempInt;
                if (l1.next != null || l2.next != null)
                    temp.next = new ListNode(0);
            }

            l1 = l1.next;
            l2 = l2.next;
            temp = temp.next;
        }
        if (flag){
            temp = result;
            while (temp != null){
                if (temp.val >= 10) {
                    temp.val = temp.val % 10;
                    if (temp.next != null)
                        temp.next.val += 1;
                    else
                        temp.next = new ListNode(1);
                }
                temp = temp.next;
            }
        }

        return result;
    }
}
```

代码存在优化的地方，用不到这么多if-else。

## 231.Power of Two

解法1 ：利用短除法的思想，不断的/2，若最后除得值为1，则该数符合2的N次方

```
public class Solution {
    public boolean isPowerOfTwo(int n) {
        if(n == 0) return false;
        while(n%2 == 0) n /= 2;
        if( n == 1 ) return true;
        else return false;
    }
}
```

解法2：利用位运算

```
public class Solution {
    public boolean isPowerOfTwo(int n) {
        return n > 0 && (n==(n & -n));
    }
}
```

假设一个数是二的次方次，那么它的二进制数中必定只含有一个1，例如的8二进制是00100，则它的负数为11100（取反加一），经过与运算，得到的结果是00100，这恰好是它本身，因此，我们便可以判断出这个数是不是二的多少次方，这个算法是O（1）的，相比起解法一要快上不少。

另外这种做法实际上是可以用来统计二进制数中有多少个1

```
while（n）｛n-=n&-n；sum++;}
```

先用刚才的方法取出高位的1，再用原数减去高位1，count++，如此循环，即可计算出1的个数。

## 190\. Reverse Bits

*   Difficulty: Easy
*   Description：

    Reverse bits of a given 32 bits unsigned integer.

    For example, given input 43261596 (represented in binary as 00000010100101000001111010011100), return 964176192 (represented in binary as 00111001011110000010100101000000).

    Follow up:
    If this function is called many times, how would you optimize it?

    Related problem: Reverse Integer

    Credits:
    Special thanks to @ts for adding this problem and creating all test cases.

将一个二进制数反转，最笨的处理方法就是按位逆序，算法复杂度是O(n)

我采用的方法去寻找一种数，能够将我所需要的位数提取出来，然后通过或运算将我需要的位置进行交换，例如11010011这个数，我想将他的奇数位提取出来，即1 1 0 1四位，那么我就可以构造01010101这个数与其进行与运算，这样就可以提取出来。

同样的，我再将它的偶数位提取出来，即1 0 0 1，构造数为10101010。

接下来，我们将奇数位左移一位，即将01010001左移一位，得到10100010，将偶数位右移一位，即将10000010右一位，得到01000001。

最后，将其进行按位或运算，得到11100011，得到的这个数正好是11010011每两位互换的结果。

如此类推 我们对相邻一、两位、四位、八位、十六位进行互换之后，就可以得到一个整形的数的逆序的二进制表示（2^5 = 32，所以是五次）。

下面给出代码

```
public class Solution {

    public int reverseBits(int n) {
        n = (0x55555555 & n ) << 1 | (0xaaaaaaaa & n ) >>> 1;
        n = (0x33333333 & n ) << 2 | (0xcccccccc & n ) >>> 2;
        n = (0x0f0f0f0f & n ) << 4 | (0xf0f0f0f0 & n ) >>> 4;
        n = (0x00ff00ff & n ) << 8 | (0xff00ff00 & n ) >>> 8;
        n = (0x0000ffff & n ) << 16 | (0xffff0000 & n ) >>> 16; 
        return n;
    }
}
```

**二进制数左移最右边补0。但右移的时候分两种情况，无符号数是右移补0，这称为逻辑右移，另一种则是向右填充最高位的数字，使其不改变其符号，这叫算术右移。本题中，由于是无符号位，所以我们要使用逻辑右移填充0。**

## 289.Game of Life

*   Difficulty: Easy
*   Description：Medium

    According to the Wikipedia’s article: “The Game of Life, also known simply as Life, is a cellular automaton devised by the British mathematician John Horton Conway in 1970.”

    Given a board with m by n cells, each cell has an initial state live (1) or dead (0). Each cell interacts with its eight neighbors (horizontal, vertical, diagonal) using the following four rules (taken from the above Wikipedia article):

    Any live cell with fewer than two live neighbors dies, as if caused by under-population.
    Any live cell with two or three live neighbors lives on to the next generation.
    Any live cell with more than three live neighbors dies, as if by over-population..
    Any dead cell with exactly three live neighbors becomes a live cell, as if by reproduction.
    Write a function to compute the next state (after one update) of the board given its current state.

    Follow up:
    Could you solve it in-place? Remember that the board needs to be updated at the same time: You cannot update some cells first and then use their updated values to update other cells.
    In this question, we represent the board using a 2D array. In principle, the board is infinite, which would cause problems when the active area encroaches the border of the array. How would you address these problems?

题意为给出一个n*m的玻璃板（矩阵），每个小格子上有一个细胞，这个细胞有两个状态为生（1）和死（0），现在有四个条件，根据条件判断出次玻璃板中下一秒细胞的状态。

1.  如果一个细胞活着，且它周围8个格子中少于2个活着的细胞的时候，它会变成死亡。
2.  如果一个细胞活着，且它周围8个格子中含有2-3个活着的细胞的时候，该细胞保持原状。
3.  如果一个细胞活着，且它周围8个格子中大于3个活着的细胞的时候，该细胞死亡。
4.  如果一个细胞死亡，但它周围8个各自中恰好有3个活着的时候，该细胞转变成复活状态。

笔者没有想到什么好的算法优化方法..至少是O（mn），参考了一下别人的答案，可以从空间上面下手，例如先遍历一次，将要变换的状态用某种特殊的数字标记好，该数字应能确定该细胞变化前的状态与变化后的状态，这样才能使得别的细胞进行判定的时候发生混乱。最后再遍历一次，将所有的标记还原成1与0。

```
public class Solution {
    final static int DEAD_TO_DEAD = 0;
    final static int LIVE_TO_DEAD = 1;
    final static int DEAD_TO_LIVE = 2;
    final static int LIVE_TO_LIVE = 3;

    public boolean isAlive(int status){
        if (status % 2 == 1 ){
            return true;
        }else {
            return false;
        }
    }

    public void gameOfLife(int[][] board) {
        if (board == null)
            return;

        int height = board.length;
        if (height == 0)
            return;

        int width = board[0].length;
        if (width == 0)
            return;

        int live_count = 0;

        for (int i = 0; i < height; i++) {
            for (int j = 0; j < width; j++) {

                live_count = 0;

                if (i > 0 && j > 0 && isAlive(board[i-1][j-1]))
                    live_count++;

                if (i > 0 && isAlive(board[i-1][j]))
                    live_count++;

                if (i > 0 && j < width - 1 && isAlive(board[i-1][j+1]))
                    live_count++;

                if (j > 0 && isAlive(board[i][j-1]))
                    live_count++;

                if (j < width - 1 && isAlive(board[i][j+1]))
                    live_count++;

                if (i < height - 1 && j > 0 && isAlive(board[i+1][j-1]))
                    live_count++;

                if (i < height - 1 && isAlive(board[i+1][j]))
                    live_count++;

                if (i < height - 1 && j < width - 1 && isAlive(board[i+1][j+1]))
                    live_count++;

                if (isAlive(board[i][j])){
                    if (live_count < 2 || live_count > 3)
                        board[i][j] = LIVE_TO_DEAD;
                    else{
                        board[i][j] = LIVE_TO_LIVE;
                    }
                }else {
                    if (live_count == 3)
                        board[i][j] = DEAD_TO_LIVE;
                }
            }
        }

        for (int i = 0; i < height; i++) {
            for (int j = 0; j < width; j++) {
                if (board[i][j] == DEAD_TO_LIVE || board[i][j] == LIVE_TO_LIVE)
                    board[i][j] = 1;
                else
                    board[i][j] = 0;
            }
        }
    }
}
```

本题中，我将初始为DEAD的值标记位偶数，将初始为LIVE的值标记为奇数，这样每次判定一个格子在此次变换前是不是存在活细胞的时候，我只要判定当前值是不是奇数即可。

循环中的8个if语句对应着八个格子判断的条件，这里要注意的是一些边界格子的判定，注意数组越界，最后的部分就是将标记根据变换后状态重置。

本题实际上不难，主要是要考虑清楚怎么去处理在相邻细胞已经发生过判定的情况下，如何得知其变化前的值，一种处理方案就是多开一个数组去存，原始数组不动，只往新数组中添加数据。另一种就是如上文所述利用标记位。

## **LeetCode部分到此结束。**