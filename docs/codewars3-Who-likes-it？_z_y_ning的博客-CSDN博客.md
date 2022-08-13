<!--yml
category: codewars
date: 2022-08-13 11:40:52
-->

# codewars3 Who likes it?_z_y_ning的博客-CSDN博客

> 来源：[https://blog.csdn.net/z_y_ning/article/details/102503990?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-102503990-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/z_y_ning/article/details/102503990?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036059116782388023961%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036059116782388023961&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-102503990-null-null.142^v40^control,185^v2^control&utm_term=codewars)

****Instructions*****
You probably know the “like” system from Facebook and other pages. People can “like” blog posts, pictures or other items. We want to create the text that should be displayed next to such an item.

Implement a function likes :: [String] -> String, which must take in input array, containing the names of people who like an item. It must return the display text as shown in the examples:
likes [] // must be “no one likes this”
likes [“Peter”] // must be “Peter likes this”
likes [“Jacob”, “Alex”] // must be “Jacob and Alex like this”
likes [“Max”, “John”, “Mark”] // must be “Max, John and Mark like this”
likes [“Alex”, “Jacob”, “Mark”, “Max”] // must be “Alex, Jacob and 2 others like this”
**Solution:**

```
def likes(names):
    if len(names)==0:
        return 'no one likes this'
    elif len(names)==1:
        return names[0]+' likes this'
    elif len(names)==2:
        return names[0]+' and '+names[1]+' like this'
    elif len(names)==3:
        return names[0]+', '+names[1]+' and '+names[2]+' like this'
    else:
        for name in names:
            return names[0]+', '+names[1]+' and '+str(len(names)-2)+' others like this' 
```

附一个网上找的大神的

```
def likes(names):
    formats = {
            0: "no one likes this",
            1: "{} likes this",
            2: "{} and {} like this",
            3: "{}, {} and {} like this",
            4: "{}, {} and {others} others like this"
        }
    n = len(names)
    return formats[min(n,4)].format(*names, others=n-2) 
```