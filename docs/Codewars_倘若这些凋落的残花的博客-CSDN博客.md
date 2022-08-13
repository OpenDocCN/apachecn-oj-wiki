<!--yml
category: codewars
date: 2022-08-13 11:35:14
-->

# Codewars_倘若这些凋落的残花的博客-CSDN博客

> 来源：[https://blog.csdn.net/ldjzxn/article/details/119680958?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058416782390564658%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058416782390564658&biz_id=&utm_medium=distribute.pc_search_result.none-task-code-2~all~first_rank_ecpm_v1~rank_v31_ecpm-20-119680958-13-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/ldjzxn/article/details/119680958?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058416782390564658%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058416782390564658&biz_id=&utm_medium=distribute.pc_search_result.none-task-code-2~all~first_rank_ecpm_v1~rank_v31_ecpm-20-119680958-13-null-null.142^v40^control,185^v2^control&utm_term=codewars)

# Vowel Count

```
def getCount(s):
    return sum(c in 'aeiou' for c in s) 
```

```
import re
def getCount(str):
    return len(re.findall('[aeiou]', str, re.IGNORECASE)) 
```

# Tribonacci Sequence

*As the name may already reveal, it works basically like a Fibonacci, but summing the last 3 (instead of 2) numbers of the sequence to generate the next. And, worse part of it, regrettably I won’t get to hear non-native Italian speakers trying to pronounce it 😦*

*So, if we are to start our Tribonacci sequence with [1, 1, 1] as a starting input (AKA signature), we have this sequence:[1, 1 ,1, 3, 5, 9, 17, 31, …]*
*But what if we started with [0, 0, 1] as a signature? As starting with [0, 1] instead of [1, 1] basically shifts the common Fibonacci sequence by once place, you may be tempted to think that we would get the same sequence shifted by 2 places, but that is not the case and we would get:[0, 0, 1, 1, 2, 4, 7, 13, 24, …]*
*Well, you may have guessed it by now, but to be clear: you need to create a fibonacci function that given a signature array/list, returns the first n elements - signature included of the so seeded sequence.*

*Signature will always contain 3 numbers; n will always be a non-negative number; if n == 0, then return an empty array (except in C return NULL) and be ready for anything else which is not clearly specified 😉*

```
def tribonacci(signature, n):

    if n <= 3:
        return signature[:n]
    else:
        for i in range(n-3):
            signature.append(sum(signature[-3:]))
    return signature 
```

# Isograms

*An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore letter case.*

```
def is_isogram(string):
    return len(string) == len(set(string.lower())) 
```

# Stop gninnipS My sdroW!

*Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed (like the name of this kata).
Strings passed in will consist of only letters and spaces.
Spaces will be included only when more than one word is present.*

```
def spin_words(sentence):

    return " ".join(s.[::-1] if len(s)>=5 else s for s in sentence.split(" ")) 
```

# Ones and Zeros

*Given an array of ones and zeroes, convert the equivalent binary value to an integer.
Eg: [0, 0, 0, 1] is treated as 0001 which is the binary representation of 1.*

```
def binary_array_to_number(arr):
	return int("".join(map(str,arr)),2) 
```

# List Filtering

*In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.*

```
def filter_list(l):
    return [i for i in l if isinstance(i, int)] 
```

# Does my number look big in this?

*A Narcissistic Number is a positive number which is the sum of its own digits, each raised to the power of the number of digits in a given base. In this Kata, we will restrict ourselves to decimal (base 10).
For example, take 153 (3 digits), which is narcisstic:
1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153
and 1652 (4 digits), which isn’t:
1^4 + 6^4 + 5^4 + 2^4 = 1 + 1296 + 625 + 16 = 1938*

```
def narcissistic( value ):
    return value == sum(int(x)**len(str(value)) for x in str(value)) 
```

# Dubstep

*Polycarpus works as a DJ in the best Berland nightclub, and he often uses dubstep music in his performance. Recently, he has decided to take a couple of old songs and make dubstep remixes from them.
Let’s assume that a song consists of some number of words (that don’t contain WUB). To make the dubstep remix of this song, Polycarpus inserts a certain number of words “WUB” before the first word of the song (the number may be zero), after the last word (the number may be zero), and between words (at least one between any pair of neighbouring words), and then the boy glues together all the words, including “WUB”, in one string and plays the song at the club.
For example, a song with words “I AM X” can transform into a dubstep remix as “WUBWUBIWUBAMWUBWUBX” and cannot transform into “WUBWUBIAMWUBX”.
Recently, Jonny has heard Polycarpus’s new dubstep track, but since he isn’t into modern music, he decided to find out what was the initial song that Polycarpus remixed. Help Jonny restore the original song.
Input
The input consists of a single non-empty string, consisting only of uppercase English letters, the string’s length doesn’t exceed 200 characters
Output
Return the words of the initial song that Polycarpus used to make a dubsteb remix. Separate the words with a space.*

```
def song_decoder(song):
    return " ".join(song.replace("WUB", " ").split()) 
```

# Duplicate Encoder

*The goal of this exercise is to convert a string to a new string where each character in the new string is “(” if that character appears only once in the original string, or “)” if that character appears more than once in the original string. Ignore capitalization when determining if a character is a duplicate.*

```
def duplicate_encode(word):
    return "".join(["(" if word.lower().count(c) == 1 else ")" for c in word.lower()]) 
```

# Take a Number And Sum Its Digits Raised To The Consecutive Powers And …¡Eureka!!

*The number 89 is the first integer with more than one digit that fulfills the property partially introduced in the title of this kata. What’s the use of saying “Eureka”? Because this sum gives the same number.
In effect: 89 = 8^1 + 9^2
The next number in having this property is 135.
See this property again: 135 = 1^1 + 3^2 + 5^3
We need a function to collect these numbers, that may receive two integers a, b that defines the range [a, b] (inclusive) and outputs a list of the sorted numbers in the range that fulfills the property described above.
Let’s see some cases:
sum_dig_pow(1, 10) == [1, 2, 3, 4, 5, 6, 7, 8, 9]
sum_dig_pow(1, 100) == [1, 2, 3, 4, 5, 6, 7, 8, 9, 89]
If there are no numbers of this kind in the range [a, b] the function should output an empty list.
sum_dig_pow(90, 100) == []*

```
enumerate(sequence，int)函数的返回值（y， x）分别代表索引与索引对应的值，int是开始遍历的索引值。 
```

```
def dig_pow(n):
    return sum(int(x) ** y for y, x in enumerate(str(n), 1))
def sum_dig_pow(a, b):
    return [x for x in range(a, b + 1) if x == dig_pow(x)] 
```

# Build Tower

```
centerstr.center(width[, fillchar])
			width -- 字符串的总宽度。
			fillchar -- 填充字符。 
```

```
def tower_builder(n):
    return [("*" * (i*2-1)).center(n*2-1) for i in range(1, n+1)] 
```

# Pick peaks

*In this kata, you will write a function that returns the positions and the values of the “peaks” (or local maxima) of a numeric array.
For example, the array arr = [0, 1, 2, 5, 1, 0] has a peak at position 3 with a value of 5 (since arr[3] equals 5).
The output will be returned as an object with two properties: pos and peaks. Both of these properties should be arrays. If there is no peak in the given array, then the output should be {pos: [], peaks: []}.
Example: pickPeaks([3, 2, 3, 6, 4, 1, 2, 3, 2, 1, 2, 3]) should return {pos: [3, 7], peaks: [6, 3]} (or equivalent in other languages)
All input arrays will be valid integer arrays (although it could still be empty), so you won’t need to validate the input.
The first and last elements of the array will not be considered as peaks (in the context of a mathematical function, we don’t know what is after and before and therefore, we don’t know if it is a peak or not).
Also, beware of plateaus !!! [1, 2, 2, 2, 1] has a peak while [1, 2, 2, 2, 3] and [1, 2, 2, 2, 2] do not. In case of a plateau-peak, please only return the position and value of the beginning of the plateau. For example: pickPeaks([1, 2, 2, 2, 1]) returns {pos: [1], peaks: [2]} (or equivalent in other languages)
Have fun!*

这一题需要考虑的情况:[3,2,3,6,4,1,2,3,2,1,2,2,2,1]
[3, 2, 3, 6, 4, 1, 2, 3, 2, 1, 2, 3]
针对第一种情况出现连续的相同数字,只需记录第一个为peak,接着一直向后判断,若出现小于peak的值,则将peak加入列表.

```
def pick_peaks(arr):
    pos = []
    prob_peak = False
    for i in range(1, len(arr)):
        if arr[i] > arr[i-1]:
            prob_peak = i
        elif arr[i] < arr[i-1] and prob_peak:
            pos.append(prob_peak)
            prob_peak = False
    return {'pos':pos, 'peaks':[arr[i] for i in pos]} 
```

# <4kyu> Human readable duration format

*Your task in order to complete this Kata is to write a function which formats a duration, given as a number of seconds, in a human-friendly way.
The function must accept a non-negative integer. If it is zero, it just returns “now”. Otherwise, the duration is expressed as a combination of years, days, hours, minutes and seconds.
It is much easier to understand with an example:
format_duration(62) # returns “1 minute and 2 seconds”
format_duration(3662) # returns “1 hour, 1 minute and 2 seconds”
For the purpose of this Kata, a year is 365 days and a day is 24 hours.
Note that spaces are important.
Detailed rules
The resulting expression is made of components like 4 seconds, 1 year, etc. In general, a positive integer and one of the valid units of time, separated by a space. The unit of time is used in plural if the integer is greater than 1.
The components are separated by a comma and a space (", "). Except the last component, which is separated by " and ", just like it would be written in English.
A more significant units of time will occur before than a least significant one. Therefore, 1 second and 1 year is not correct, but 1 year and 1 second is.
Different components have different unit of times. So there is not repeated units like in 5 seconds and 1 second.
A component will not appear at all if its value happens to be zero. Hence, 1 minute and 0 seconds is not valid, but it should be just 1 minute.
A unit of time must be used “as much as possible”. It means that the function should not return 61 seconds, but 1 minute and 1 second instead. Formally, the duration specified by of a component must not be greater than any valid more significant unit of time.*

这一题的在于格式转换

```
times = [("year", 31536000),   
         ("day", 86400),
         ("hour", 3600),
         ("minute", 60),
         ("second", 1)]

def format_duration(seconds):

    if not seconds:
        return "now"

    chunks = []
    for name, secs in times:
        qty = seconds // secs                     
        if qty:                                   
            if qty > 1:                           
                name += "s"                       
            chunks.append(str(qty) + " " + name)  

        seconds = seconds % secs                  
    return ', '.join(chunks[:-1]) + ' and ' + chunks[-1] if len(chunks) > 1 else chunks[0] 
```

# <4 kyu> Recover a secret string from random triplets

*There is a secret string which is unknown to you. Given a collection of random triplets from the string, recover the original string.
A triplet here is defined as a sequence of three letters such that each letter occurs somewhere before the next in the given string. “whi” is a triplet for the string “whatisup”.
As a simplification, you may assume that no letter occurs more than once in the secret string.
You can assume nothing about the triplets given to you other than that they are valid triplets and that they contain sufficient information to deduce the original string. In particular, this means that the secret string will never contain letters that do not occur in one of the triplets given to you.*

```
def recoverSecret(triplets):
    r = list(set([i for l in triplets for i in l]))
    r.sort()  
    for l in triplets:
        fix(r, l[1], l[2])
        fix(r, l[0], l[1])
    return ''.join(r)

def fix(l, a, b):
    """let l.index(a) < l.index(b)"""
    if l.index(a) > l.index(b):
        l.remove(a)
        l.insert(l.index(b), a) 
```

```
def recoverSecret(a):
    out = list(zip(*a))       
    h = [j for j in (set(out[0]) - set(out[1] + out[2]))]  
    for i in a:                          
        if i[0] in h:                    
            i[:2], i[2] = i[1:], ''      

    return h[0] + recoverSecret(a) if h else str() 
```

# <4kyu> Sum of Intervals

*Write a function called sumIntervals/sum_intervals() that accepts an array of intervals, and returns the sum of all the interval lengths. Overlapping intervals should only be counted once.
Intervals
Intervals are represented by a pair of integers in the form of an array. The first value of the interval will always be less than the second value. Interval example: [1, 5] is an interval from 1 to 5\. The length of this interval is 4.
Overlapping Intervals
List containing overlapping intervals:
[
[1,4],
[7, 10],
[3, 5]
]
The sum of the lengths of these intervals is 7\. Since [1, 4] and [3, 5] overlap, we can treat the interval as [1, 5], which has a length of 4.
Examples:
sumIntervals( [
[1,2],
[6, 10],
[11, 15]
] ); // => 9
sumIntervals( [
[1,4],
[7, 10],
[3, 5]
] ); // => 7
sumIntervals( [
[1,5],
[10, 20],
[1, 6],
[16, 19],
[5, 11]
] ); // => 19*

```
def sum_of_intervals(intervals):
    result = set()
    for start, stop in intervals:
        for x in range(start, stop):
            print(x)
            result.add(x)

    return len(result) 
```