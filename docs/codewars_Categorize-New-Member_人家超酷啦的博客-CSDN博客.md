<!--yml
category: codewars
date: 2022-08-13 11:43:59
-->

# codewars_Categorize New Member_人家超酷啦的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_43389623/article/details/104816773?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-104816773.nonecase](https://blog.csdn.net/qq_43389623/article/details/104816773?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-104816773.nonecase)

**goal:** Output will consist of a list of string values (in Haskell: Open or Senior) stating whether the respective member is to be placed in the senior or open category.

**’Senior’**:To be a senior, a member must be at least 55 years old and have a handicap greater than 7.

**Input:** [[18, 20], [45, 2], [61, 12], [37, 6],[21, 21], [78, 9]]

```
def openOrSenior(data)
	res=[]
	for item in data:
		if item[0]>54 and item[1]>7:
			res.append('senior')
		else:
			res.append('Open')
	return res; 
```

**Clever**

```
def openOrSenior(data)
	return ['Senior' if age > 54 and handicap > 7 else 'Open' for (age, handicap) in data] 
```

> The (x,y) syntax in these sort of loops will perform tuple unpacking.

> This is same sort of syntax as: a,b = [1, 2], or (a,b) = [1,2]