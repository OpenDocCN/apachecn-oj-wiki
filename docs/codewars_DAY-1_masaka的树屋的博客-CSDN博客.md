<!--yml
category: codewars
date: 2022-08-13 11:47:54
-->

# codewars_DAY 1_masaka的树屋的博客-CSDN博客

> 来源：[https://blog.csdn.net/xwcqqq/article/details/52573548?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-52573548.nonecase](https://blog.csdn.net/xwcqqq/article/details/52573548?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-52573548.nonecase)

*The goal of this exercise is to convert a string to a new string where each character in the new string is ‘(’ if that character appears only once in the original string, or ‘)’ if that character appears more than once in the original string. Ignore capitalization when determining if a character is a duplicate.*

```
 Examples:

    "din" => "((("

    "recede" => "()()()"

    "Success" => ")())())"

    "(( @" => "))((" 
```

* * *

*Write a function called validParentheses that takes a string of parentheses, and determines if the order of the parentheses is valid. validParentheses should return true if the string is valid, and false if it’s invalid.*

```
 Examples: 
    validParentheses( "()" ) => returns true 
    validParentheses( ")(()))" ) => returns false 
    validParentheses( "(" ) => returns false 
    validParentheses( "(())((()())())" ) => returns true 
```

*All input strings will be nonempty, and will only consist of open parentheses ‘(’ and/or closed parentheses ‘)’*

*   my answer

    ```
    def valid_parentheses(string):
        if string.count('(') != string.count(')'):
            return False
        l = []
        for i in string:
            if i == '(':
                l.append('(')
            elif i == ')':
                if len(l) == 0:
                    return False
                if l.pop() != '(':
                    return False
        return len(l) == 0 
    ```

*   best answer

    ```
    def valid_parentheses(string):
        cnt = 0
        for char in string:
            if char == '(': cnt += 1
            if char == ')': cnt -= 1
            if cnt < 0: return False
        return True if cnt == 0 else False 
    ```

* * *

*Given a list of integers and a single sum value, return the first two values (parse from the left please) in order of appearance that add up to form the sum.*

```
 sum_pairs([11, 3, 7, 5],         10)
    #              ^--^      3 + 7 = 10
    == [3, 7]

    sum_pairs([4, 3, 2, 3, 4],         6)
    #          ^-----^         4 + 2 = 6, indices: 0, 2 *
    #             ^-----^      3 + 3 = 6, indices: 1, 3
    #                ^-----^   2 + 4 = 6, indices: 2, 4
    #  * entire pair is earlier, and therefore is the correct answer
    == [4, 2]

    sum_pairs([0, 0, -2, 3], 2)
    #  there are no pairs of values that can be added to produce 2.
    == None/nil/undefined (Based on the language)

    sum_pairs([10, 5, 2, 3, 7, 5],         10)
    #              ^-----------^   5 + 5 = 10, indices: 1, 5
    #                    ^--^      3 + 7 = 10, indices: 3, 4 *
    #  * entire pair is earlier, and therefore is the correct answer
    == [3, 7] 
```

*Negative numbers and duplicate numbers can and will appear.*

*NOTE: There will also be lists tested of lengths upwards of 10,000,000 elements. Be sure your code doesn’t time out.*

*   best answer *

    ```
    def sum_pairs(lst, s):
        cache = set()
        for i in lst:
            if s - i in cache:
                return [s - i, i]
            cache.add(i) 
    ```

*   my answer

    ```
    # time out
    def sum_pairs(ints, s):
    right = []
    tmp = len(ints) + 1
    for i, p in enumerate(ints):
        for j, q in enumerate(ints[i+1:]):
            if i > tmp:
                break
            if p + q == s:
                if not right:
                    right.extend([p,q])
                    tmp = j + i
                elif j + i< tmp:
                    (right[0],right[1]) = (p,q)
                    tmp = j + i
    return right if right else None 
    ```