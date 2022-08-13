<!--yml
category: codewars
date: 2022-08-13 11:40:58
-->

# 【Codewars】Josephus Permutation_1000sakura的博客-CSDN博客

> 来源：[https://blog.csdn.net/ecysakura/article/details/90722455?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-90722455.142^v40^control,185^v2^control](https://blog.csdn.net/ecysakura/article/details/90722455?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-90722455.142^v40^control,185^v2^control)

### Codewars里的 5kyu Kata。

### 题目说明：

> This problem takes its name by arguably the most important event in the life of the ancient historian Josephus: according to his tale, he and his 40 soldiers were trapped in a cave by the Romans during a siege.
> 
> Refusing to surrender to the enemy, they instead opted for mass suicide, with a twist: **they formed a circle and proceeded to kill one man every three, until one last man was left (and that it was supposed to kill himself to end the act)**.
> 
> Well, Josephus and another man were the last two and, as we now know every detail of the story, you may have correctly guessed that they didn't exactly follow through the original idea.
> 
> You are now to create a function that returns a Josephus permutation, taking as parameters the initial *array/list of items* to be permuted as if they were in a circle and counted out every *k* places until none remained.
> 
> **Tips and notes:** it helps to start counting from 1 up to n, instead of the usual range 0..n-1; k will always be >=1.
> 
> For example, with n=7 and k=3 `josephus(7,3)` should act this way.
> 
> ```
> [1,2,3,4,5,6,7] - initial sequence
> [1,2,4,5,6,7] => 3 is counted out and goes into the result [3]
> [1,2,4,5,7] => 6 is counted out and goes into the result [3,6]
> [1,4,5,7] => 2 is counted out and goes into the result [3,6,2]
> [1,4,5] => 7 is counted out and goes into the result [3,6,2,7]
> [1,4] => 5 is counted out and goes into the result [3,6,2,7,5]
> [4] => 1 is counted out and goes into the result [3,6,2,7,5,1]
> [] => 4 is counted out and goes into the result [3,6,2,7,5,1,4]
> ```
> 
> So our final result is:
> 
> ```
> josephus([1,2,3,4,5,6,7],3)==[3,6,2,7,5,1,4]
> ```
> 
> For more info, browse the [Josephus Permutation](http://en.wikipedia.org/wiki/Josephus_problem) page on wikipedia; related kata: [Josephus Survivor](http://www.codewars.com/kata/josephus-survivor).

### 解题代码：

```
import java.util.List;
import java.util.ArrayList;

public class Josephus {
    public static <T> List<T> josephusPermutation(final List<T> items, final int k) {
        List<T> res = new ArrayList<T>();
        int count = items.size();
        int i = 0;
        while(count > 0){
            i = (i + k - 1)%items.size();
            res.add(items.remove(i));
            count--;
        }
        return res;
    }
}
```

Test Cases:

```
import static org.hamcrest.CoreMatchers.is;
import static org.junit.Assert.assertThat;

import java.util.ArrayList;
import java.util.List;
import java.util.Arrays;
import java.util.Random;

import org.junit.Test;

public class JosephusTest {

    private static int NUM_RANDOM_TESTS = 40;
    private static int MAX_ITEMS = 50;
    private static int MAX_ITEM_VALUE = 200;
    private static int MAX_K = 20;

    @Test
    public void test1() {
        josephusTest(new Object[] { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 }, 1, new Object[] { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 });
    }

    @Test
    public void test2() {
        josephusTest(new Object[] { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 }, 2, new Object[] { 2, 4, 6, 8, 10, 3, 7, 1, 9, 5 });
    }

    @Test
    public void test3() {
        josephusTest(new Object[] { "C", "o", "d", "e", "W", "a", "r", "s" }, 4,
                new Object[] { "e", "s", "W", "o", "C", "d", "r", "a" });
    }

    @Test
    public void test4() {
        josephusTest(new Object[] { 1, 2, 3, 4, 5, 6, 7 }, 3, new Object[] { 3, 6, 2, 7, 5, 1, 4 });
    }

    @Test
    public void test5() {
        josephusTest(new Object[] {}, 3, new Object[] {});
    }

    @Test
    public void test6() {
        josephusTest(new Object[] { "C", 0, "d", 3, "W", 4, "r", 5 }, 4,
                new Object[] { 3, 5, "W", 0, "C", "d", "r", 4 });
    }

    @Test
    public void test7() {
        josephusTest(
                new Object[] { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24,
                        25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48,
                        49, 50 },
                11,
                new Object[] { 11, 22, 33, 44, 5, 17, 29, 41, 3, 16, 30, 43, 7, 21, 36, 50, 15, 32, 48, 14, 34, 1, 20,
                        39, 9, 28, 2, 25, 47, 24, 49, 27, 8, 38, 19, 6, 42, 35, 26, 23, 31, 40, 4, 18, 12, 13, 46, 37,
                        45, 10 });
    }

    @Test
    public void test8() {
        josephusTest(new Object[] { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15 }, 40,
                new Object[] { 10, 7, 8, 13, 5, 4, 12, 11, 3, 15, 14, 9, 1, 6, 2 });
    }

    @Test
    public void test9() {
        josephusTest(new Object[] { 1 }, 3, new Object[] { 1 });
    }

    @Test
    public void test10() {
        josephusTest(new Object[] { true, false, true, false, true, false, true, false, true }, 9,
                new Object[] { true, true, true, false, false, true, false, true, false });
    }

    @Test
    public void randomTest() {
        Random random = new Random();
        for (int i = 0; i < NUM_RANDOM_TESTS; i++) {
            List<Object> items = new ArrayList<Object>();
            for (int j = 0; j < random.nextInt(MAX_ITEMS); j++) {
                items.add(random.nextInt(MAX_ITEM_VALUE));
            }
            int k = random.nextInt(MAX_K - 1) + 1;
            assertThat(Josephus.josephusPermutation(new ArrayList<Object>(items), k),
                    is(solution(new ArrayList<Object>(items), k)));
        }
    }

    private void josephusTest(final Object[] items, final int k, final Object[] result) {
        assertThat(Josephus.josephusPermutation(new ArrayList<Object>(Arrays.asList(items)), k),
                is(Arrays.asList(result)));
    }

    private List<Object> solution(final List<Object> items, final int k) {
        List<Object> permutation = new ArrayList<Object>();
        int position = 0;
        while (items.size() > 0) {
            position = (position + k - 1) % items.size();
            permutation.add(items.remove((int) position));
        }
        return permutation;
    }
}
```

### 个人总结：

```
import java.util.List;
import java.util.LinkedList;
import java.util.ArrayList;
import java.util.Iterator;

public class Josephus {
    public static <T> List<T> josephusPermutation(List<T> items, int k) {
        List<T> permutation = new ArrayList<T>(items.size());
        CircularIterator<T> iterator = new CircularIterator<>(new LinkedList<T>(items));
        while (iterator.hasNext()) {
            iterator.skip(k - 1);
            permutation.add(iterator.next());
            iterator.remove();
        }
        return permutation;
    }

    static class CircularIterator<T> implements Iterator<T> {
        private final List<T> list;
        private Iterator<T> iterator;

        CircularIterator(List<T> list) {
            this.list = list;
            this.iterator = list.iterator();
        }

        @Override
        public boolean hasNext() {
            return !list.isEmpty();
        }

        @Override
        public T next() {
            if (!iterator.hasNext()) {
                iterator = list.iterator();
            }
            return iterator.next();
        }

        public void skip(int n) {
            while (--n >= 0 && hasNext()) {
                next();
            }
        }

        @Override
        public void remove() {
            iterator.remove();
        }
    }
}
```

```
import java.util.ArrayList;
import java.util.List;

public class Josephus {
    public static <T> List<T> josephusPermutation(final List<T> items, final int k) {
        JosephusList<T> josephus = JosephusList.create(items);
        List<T> result = new ArrayList<>();
        while (!josephus.isEmpty()) {
            josephus.movePosition(k);
            result.add(josephus.executeCurrent());
        }

        return result;
    }
}

class JosephusList<T> {
    private class JosephusNode<T> {
        T value;
        JosephusNode next;
        JosephusNode previous;

        JosephusNode(T value) {
            this.value = value;
            next = null;
            previous = null;
        }
    }

    private JosephusNode<T> start;
    private JosephusNode<T> end;
    private int size;
    private JosephusNode<T> currentPosition;

    private JosephusList() {
        this.start = null;
        this.end = null;
    }

    private void addNode(T value) {
        addNode(new JosephusNode<>(value));
    }

    private void addNode(JosephusNode<T> node) {
        if (start == null) {
            start = node;
            end = node;
            start.next = start;
            start.previous = start;
        } else {
            end.next = node;
            node.next = start;
            node.previous = end;
            start.previous = node;
            end = node;
        }

        size++;
    }

    public void movePosition(int numberOfMoves) {
        for (int i = 0; i < numberOfMoves; i++) {
            currentPosition = currentPosition.next;
        }
    }

    public T executeCurrent() {
        if (isEmpty())
            throw new IllegalArgumentException();

        JosephusNode<T> deadNode = currentPosition;
        deadNode.previous.next = deadNode.next;
        deadNode.next.previous = deadNode.previous;
        currentPosition = deadNode.previous;
        size--;

        return deadNode.value;
    }

    public boolean isEmpty() {
        return size <= 0;
    }

    public static <T> JosephusList<T> create(List<T> values) {
        JosephusList<T> josephusList = new JosephusList<>();
        for (int i = 0; i < values.size(); i++) {
            josephusList.addNode(values.get(i));
        }
        josephusList.currentPosition = josephusList.end;
        return josephusList;
    }
}
```

```
import java.util.List;
import java.util.ArrayList;

public class Josephus {
    public static <T> List<T> josephusPermutation(final List<T> items, final int k) {
        List<T> result = new ArrayList<>();
        int i = 0;
        int count = 1;
        int size = items.size();
        while (result.size() < size) {
            if (count % k == 0) {
                result.add(items.get(i));
                items.remove(i);
                if (i >= items.size())
                    i = 0;
            } else
                i = i < items.size() - 1 ? i + 1 : 0;
            count++;
        }
        return result;
    }

}
```