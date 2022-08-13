<!--yml
category: codewars
date: 2022-08-13 11:44:51
-->

# CodeWars:Decode the Morse code_lkangkang的博客-CSDN博客

> 来源：[https://blog.csdn.net/lkangkang/article/details/82698307?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-82698307.nonecase](https://blog.csdn.net/lkangkang/article/details/82698307?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-82698307.nonecase)

Part of Series 1/3

This kata is part of a series on the Morse code. After you solve this kata, you may move to the [next one](https://www.codewars.com/kata/decode-the-morse-code-advanced).

In this kata you have to write a simple [Morse code](https://en.wikipedia.org/wiki/Morse_code) decoder. While the Morse code is now mostly superceded by voice and digital data communication channels, it still has its use in some applications around the world.

The Morse code encodes every character as a sequence of "dots" and "dashes". For example, the letter `A` is coded as `·−`, letter `Q` is coded as `−−·−`, and digit `1` is coded as `·−−−−`. The Morse code is case-insensitive, traditionally capital letters are used. When the message is written in Morse code, a single space is used to separate the character codes and 3 spaces are used to separate words. For example, the message `HEY JUDE` in Morse code is `···· · −·−− ·−−− ··− −·· ·`.

**NOTE:** Extra spaces before or after the code have no meaning and should be ignored.

In addition to letters, digits and some punctuation, there are some special service codes, the most notorious of those is the international distress signal [SOS](https://en.wikipedia.org/wiki/SOS) (that was first issued by [Titanic](https://en.wikipedia.org/wiki/RMS_Titanic)), that is coded as `···−−−···`. These special codes are treated as single special characters, and usually are transmitted as separate words.

Your task is to implement a function that would take the morse code as input and return a decoded human-readable string.

For example:

```
decodeMorse('.... . -.--   .--- ..- -.. .')
#should return "HEY JUDE" 
```

**NOTE:** For coding purposes you have to use ASCII characters `.` and `-`, not Unicode characters.

The Morse code table is preloaded for you as a dictionary, feel free to use it:

*   Coffeescript/C++/Go/JavaScript/PHP/Python/Ruby/TypeScript: `MORSE_CODE['.--']`
*   C#: `MorseCode.Get(".--")` (returns `string`)
*   Elixir: `morse_codes` variable
*   Haskell: `morseCodes ! ".--"` (Codes are in a `Map String String`)
*   Java: `MorseCode.get(".--")`
*   Kotlin: `MorseCode[".--"] ?: ""` or `MorseCode.getOrDefault(".--", "")`
*   Rust: `self.morse_code`

All the test strings would contain valid Morse code, so you may skip checking for errors and exceptions. In C#, tests will fail if the solution code throws an exception, please keep that in mind. This is mostly because otherwise the engine would simply ignore the tests, resulting in a "valid" solution.

Good luck!

After you complete this kata, you may try yourself at [Decode the Morse code, advanced](http://www.codewars.com/kata/decode-the-morse-code-advanced).

my solution:

思路不难，就是搞那个空格搞了好久。要先把头尾空格去掉，然后明白字母之间有一个空格，单词之间有三个空格就可以了。不要用它提供的return.

```
def decodeMorse(morse_code):
    # ToDo: Accept dots, dashes and spaces, return human-readable message
    morse_code = morse_code.strip().split(' ')
    a=[]
    space=0
    for i,one in enumerate(morse_code):
        if one == '':
            space += 1
        else:
            if space>1:
                a.append(' ')
            a.append(MORSE_CODE[one])
            print one,' ',MORSE_CODE[one]
            space = 0
    morse_code=''.join(a)
    return morse_code#.replace('.', MORSE_CODE['.']).replace('-', MORSE_CODE['-'])#.replace(' ', '')
```

 cleverest solution:

[WOnder93](https://www.codewars.com/users/WOnder93), [Darigaaz](https://www.codewars.com/users/Darigaaz), [HEXecutive](https://www.codewars.com/users/HEXecutive), [shreyassaxena](https://www.codewars.com/users/shreyassaxena), [korchak](https://www.codewars.com/users/korchak), [grabks](https://www.codewars.com/users/grabks) (plus 20 more warriors)

```
def decodeMorse(morseCode):
    return ' '.join(''.join(MORSE_CODE[letter] for letter in word.split(' ')) for word in morseCode.strip().split('   '))
```