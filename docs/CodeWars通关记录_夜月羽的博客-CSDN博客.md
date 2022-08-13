<!--yml
category: codewars
date: 2022-08-13 11:32:38
-->

# CodeWars通关记录_夜月羽的博客-CSDN博客

> 来源：[https://blog.csdn.net/u012138457/article/details/104305277?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-104305277.142^v40^control,185^v2^control](https://blog.csdn.net/u012138457/article/details/104305277?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-9-104305277.142^v40^control,185^v2^control)

2020-2-13
**Jaden Casing Strings**

```
 def to_jaden_case(string):
    if string.find(" ")<0:
        return string.capitalize()
    else:
        return string.split(" ",1)[0].capitalize()+" "+to_jaden_case(string.split(" ",1)[1])

def to_jaden_case(string):        
    return " ".join(w.capitalize() for w in string.split()) 
```

2020-2-14
**Beginner Series #3 Sum of Numbers**

```
 import math
def get_sum(a,b):
    list=[]
    list.extend(range(a,b,((b-a)>0)*2-1))
    list.append(b)
    return sum(list)

def get_sum(a,b):
    return sum(range(min(a,b), max(a,b)+1)) 
```

**Get the Middle Character**

```
 def get_middle(s):
    return s[int((len(s)+1)/2-1):int((len(s)+2)/2)]

def get_middle(s):
   return s[(len(s)-1)/2:len(s)/2+1] 
```

**Get the Middle Character**

```
 def spin_words(sentence):
    return " ".join([x[::-1] if len(x)>=5 else x for x in sentence.split()])

def spin_words(sentence):
    words = [word for word in sentence.split(" ")]
    words = [word if len(word) < 5 else word[::-1] for word in words]
    return " ".join(words) 
```

2020-2-17
**Where my anagrams at?**

```
 def anagrams(word, words):      
    cmp_dict = dict([[x, word.count(x)] for x in word])
    result = words.copy()
    for i in words:
        if len(i)!=len(word):
            result.remove(i)
        else:
            for j in cmp_dict.keys():
                if i.count(j)!=cmp_dict[j]:
                    result.remove(i)
                    break
    return result

def anagrams(word, words): 
	return [item for item in words if sorted(item)==sorted(word)]

def anagrams(word, words):
    return filter(lambda x: sorted(word) == sorted(x), words) 
```

2020-2-18
**Valid Braces**

```
 def validBraces(string):
  if string=='':
      return True
  elif len(string)%2==1:
      return False
  bracesleft = ['(','[','{']
  bracesright = [')',']','}']
  for i in range(1,len(string)):
      if  string[i] in bracesright:
          if string[i-1]==bracesleft[bracesright.index(string[i])]:
              return validBraces(string[:(i-1)]+string[(i+1):])
          else: 
              return False
  return False

def validBraces(s):
  while '{}' in s or '()' in s or '[]' in s:
      s=s.replace('{}','')
      s=s.replace('[]','')
      s=s.replace('()','')
  return s==''

def validBraces(s, previous = ''):
  while s != previous: previous, s = s, s.replace('[]','').replace('{}','').replace('()','')
  return not s 
```

**Valid Parentheses**

```
 def valid_parentheses(string):

    s="".join(filter(lambda x: x in '()', list(string)))
    while '()' in s:
        s=s.replace('()','')
    return s==''

def valid_parentheses(string):
    string = "".join(ch for ch in string if ch in "()")
    while "()" in string: 
    	string = string.replace("()", "")
    return not string 
```

2020-2-19
**Unique In Order**

```
 def unique_in_order(iterable):
    if len(iterable)>1:
        return [iterable[0]]+list(filter(lambda x: x,[y if x!=y else False for x,y in zip(iterable[:-1],iterable[1:])]))
    else:
        return list(iterable)

from itertools import groupby
def unique_in_order(iterable):
    return [k for (k, _) in groupby(iterable)]

unique_in_order = lambda l: [z for i, z in enumerate(l) if i == 0 or l[i - 1] != z] 
```

**Delete occurrences of an element if it occurs more than n times**

```
 def delete_nth(order,max_e):
    new_order=[]
    for i in order:
        if new_order.count(i)<max_e:
            new_order.append(i)
    return new_order 
```

2020-2-20
**First non-repeating character**

```
 def first_non_repeating_letter(string):
    for i in range(len(string)):
        if string.lower().count(string.lower()[i])==1:
            return string[i]
    return ''

def first_non_repeating_letter(string):
    singles = [i for i in string if string.lower().count(i.lower()) == 1]
    return singles[0] if singles else '' 
```

**Human readable duration format**

```
 def format_duration(seconds):
    l=[('year', 60*60*24*365), ('day', 60*60*24), ('hour', 60*60), ('minute', 60), ('second', 1)]
    r=[]
    for s,h in l:
        if seconds//h >= 1:
            r.extend([str(int(seconds/h)) + ' ' + s + ('s' if seconds//h > 1 else '')])
        seconds %= h
    if len(r) == 0:
        return 'now'
    elif len(r) == 1:
        return r[0]
    else:
        return ', '.join(r[:-1]) + ' and ' + r[-1]

def format_duration(seconds):
    if seconds == 0: return "now"
    units = ( (31536000, "year"  ), 
              (   86400, "day"   ),
              (    3600, "hour"  ),
              (      60, "minute"),
              (       1, "second") )
    ts, t = [], seconds
    for unit in units:
        u, t = divmod(t, unit[0])
        ts += ["{} {}{}".format(u, unit[1], "s" if u>1 else "")] if u != 0 else []
    return ", ".join([str(d)for d in ts[:-1]]) + (" and " if len(ts)>1 else "") + ts[-1] 
```

**Number of trailing zeros of N!**

```
 def zeros(n):
    k = 0
    while n>=5:
        n = n // 5
        k += n
    return k 
```

2020-2-21
**String incrementer**

```
 def increment_string(strng):
    s=0
    for i in range(len(strng)-1,-1,-1):
        if not strng[i].isdigit():
            return strng[:i+1]+str(int(s)+1)
        s=strng[i]+(s if s!=0 else '')
        if strng[i]!='9':
            return strng[:i]+str(int(s)+1)   
    return str(int(strng)+1 if strng.isdigit() else 1)

def increment_string(strng):
    head = strng.rstrip('0123456789')
    tail = strng[len(head):]
    if tail == "": return strng+"1"
    return head + str(int(tail) + 1).zfill(len(tail))

def increment_string(s):
    if s and s[-1].isdigit():
        return increment_string(s[:-1]) + "0" if s[-1] == "9" else s[:-1] + `int(s[-1]) + 1`
    return s + "1" 
```

**Product of consecutive Fib numbers**

```
 def productFib(prod):
    f1,f2=0,1
    while f1*f2<prod:
        f1,f2=f2,f1+f2
    return [f1,f2,f1*f2==prod] 
```

**My smallest code interpreter (aka Brainf**k)**

```
 def brain_luck(code, program_input):
    c=[chr(0)]
    p=0
    program_output=''
    codep=0
    while codep<len(code):
        i=code[codep]
        if i=='>': 
            p+=1
            if p==len(c): c.append(chr(0))
        if i=='<': p-=1
        if i=='+': c[p]=chr((ord(c[p])+1)%256)
        if i=='-': c[p]=chr((ord(c[p])-1)%256)
        if i=='.': program_output+=c[p]
        if i==',': 
            c[p]=program_input[0]
            program_input=program_input[1:]
        if i=='[' and ord(c[p])==0:
            flag=1
            while flag!=0:
                codep+=1
                if code[codep]=='[': flag+=1
                if code[codep]==']': flag-=1
        if i==']' and ord(c[p])!=0:
            flag=-1
            while flag!=0:
                codep-=1
                if code[codep]=='[': flag+=1
                if code[codep]==']': flag-=1
        codep+=1
    return program_output

def brain_luck(code, input_):
    vars_ = {'m': [0], 'p': 0, 'i': map(ord, input_), 'ip': 0, 'o': []}
    py_lines = []
    indent = 0
    for c in code:
        cur_indent = indent
        if   c == '>': line = 'p += 1; p != len(m) or m.append(0)'
        elif c == '<': line = 'p -= 1'
        elif c == '+': line = 'm[p] = (m[p] + 1) % 256'
        elif c == '-': line = 'm[p] = (m[p] - 1) % 256'
        elif c == '.': line = 'o.append(m[p])'
        elif c == ',': line = 'm[p] = i[ip]; ip += 1'
        elif c == '[': line = 'while m[p]:'; indent += 1
        elif c == ']': line = ''; indent -= 1
        py_lines.append('\t' * cur_indent + line)
    exec('\n'.join(py_lines), vars_)
    return ''.join(map(chr, vars_['o'])) 
```

2020-2-22
**Did I Finish my Sudoku?**

```
 def done_or_not(board): 

    for i in range(9):
        if set(board[i])!=set([1,2,3,4,5,6,7,8,9]): return 'Try again!'
        if set([x[i] for x in board])!=set([1,2,3,4,5,6,7,8,9]): return 'Try again!'

    for i,j in [(0,0),(0,3),(0,6),(3,0),(3,3),(3,6),(6,0),(6,3),(6,6)]:
        if set([board[i][j],board[i][j+1],board[i][j+2],
                board[i+1][j],board[i+1][j+1],board[i+1][j+2],
                board[i+2][j],board[i+2][j+1],board[i+2][j+2],
                ])!=set([1,2,3,4,5,6,7,8,9]): return 'Try again!'
    return 'Finished!'

import numpy as np
def done_or_not(aboard): 
  board = np.array(aboard)

  rows = [board[i,:] for i in range(9)]
  cols = [board[:,j] for j in range(9)]
  sqrs = [board[i:i+3,j:j+3].flatten() for i in [0,3,6] for j in [0,3,6]]

  for view in np.vstack((rows,cols,sqrs)):
      if len(np.unique(view)) != 9:
          return 'Try again!'

  return 'Finished!' 
```

2020-2-24
**Double Cola**

```
 from math import log
def who_is_next(names, r):
    n=int(log((r-1)//len(names)+1,2))
    return names[(r-len(names)*(2**n-1)-1)//(2**n)]

def whoIsNext(names, r):
    while r > 5:
        r = (r - 4) / 2
    return names[r-1] 
```

2020-2-27
**Sudoku Solver**

```
 import numpy as np
def CanOrNot(x,a,b,l):
    if x in l[a,:]: return False
    if x in l[:,b]: return False
    if x in l[(a//3*3):(a//3*3+3),(b//3*3):(b//3*3+3)].flatten(): return False
    return True

def sudoku(puzzle):
    """return the solved puzzle as a 2d array of 9 x 9"""
    mat=np.array(puzzle)
    pos=[[list(range(1,10)) for i in range(9)] for j in range(9)]
    temp=np.zeros((9,9))
    count=1
    while not (temp==mat).all():
        temp=mat.copy()
        for m,n in [(a,b) for a in range(9) for b in range(9)]:
            if mat[m,n]!=0:
                pos[m][n]=[mat[m,n]]
                continue
            pos_temp=[]
            for k in pos[m][n]:
                if CanOrNot(k,m,n,mat): pos_temp.append(k)
            pos[m][n]=pos_temp
            if len(pos_temp)==1:
                mat[m,n]=pos_temp[0]
        count+=1
    return mat.tolist()

from itertools import product

def possibles(puzzle, x, y):
    a, b = 3*(x/3), 3*(y/3)
    square = set([puzzle[r][c] for r, c in product(range(a,a + 3), range(b,b + 3))])
    row = set(puzzle[x])
    col = set(zip(*puzzle)[y])
    return set(range(1,10)).difference(square.union(row).union(col))

def sudoku(puzzle):
    z = [(r,c) for (r,c) in product(range(9),range(9)) if puzzle[r][c] == 0]    
    if z == []: 
        return puzzle
    for (r,c) in z:
        p = possibles(puzzle, r, c)
        if len(p) == 1:
            puzzle[r][c] = p.pop()
    return sudoku(puzzle) 
```

**The observed PIN**

```
 from itertools import product
def get_possible(n):
    if n=='1':
        return ['1','2','4']
    elif n=='2':
        return ['1','2','3','5']
    elif n=='3':
        return ['2','3','6']
    elif n=='4':
        return ['1','4','5','7']
    elif n=='5':
        return ['2','4','5','6','8']
    elif n=='6':
        return ['3','5','6','9']
    elif n=='7':
        return ['4','7','8']
    elif n=='8':
        return ['5','7','8','9','0']
    elif n=='9':
        return ['6','8','9']
    else:
        return ['0','8']

def get_pins(observed):
    '''TODO: This is your job, detective!'''
    attempt=[]
    for i in observed:
        attempt.append(get_possible(i)) 
    result=[]
    for s in product(*attempt):
        result.append("".join(s))
    return result

from itertools import product

ADJACENTS = ('08', '124', '2135', '326', '4157', '52468', '6359', '748', '85790', '968')

def get_pins(observed):
    return [''.join(p) for p in product(*(ADJACENTS[int(d)] for d in observed))] 
```

* * *