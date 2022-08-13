<!--yml
category: codewars
date: 2022-08-13 11:37:49
-->

# codewars练习（javascript）-2021/2/28_ZellaWanJY的博客-CSDN博客

> 来源：[https://blog.csdn.net/FemaleHacker/article/details/114208440?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-114208440.142^v40^control,185^v2^control](https://blog.csdn.net/FemaleHacker/article/details/114208440?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-114208440.142^v40^control,185^v2^control)

## codewars-js练习

### 2021/2/28

#### github 地址

[my github地址，上面有做的习题记录，不断更新…](https://github.com/Mszmy/Codewars/)

#### 【1】<6kyu>【Determine the date by the day number】

What date corresponds to the `n`th day of the year?
The answer depends on whether the year is a leap year or not.

Write a function that will help you determine the date if you know the number of the day in the year, as well as whether the year is a leap year or not.
The function accepts the day number and a boolean value `isLeap` as arguments, and returns the corresponding date of the year as a string `"Month, day"`.
Only valid combinations of a day number and `isLeap` will be tested.

**<mark>example</mark>**：

```
getDay(41, false)   =>  "February, 10"  
getDay(60, false)   =>  "March, 1"      
getDay(60, true)    =>  "February, 29"  
getDay(365, false)  =>  "December, 31"  
getDay(366, true)   =>  "December, 31" 
```

<mark>**solution**</mark>

```
<script type="text/javascript"> function getDay(day, isLeap){

            let days_of_year = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
            let temp = [31,59,90,120,151,181,212,243,273,304,334,365]
            if(isLeap){
                days_of_year[1] = 29
                let temp2 = [31,60,91,121,152,182,213,244,274,305,335,366]
                let result = monthDay(day,temp2,days_of_year);
                return result

                }else{
                    let result = monthDay(day,temp,days_of_year);
                    return result
                }
        }
        function monthDay(day,arr,days_of_year){
            let info = {1:'January',2:'February',3:'March',4:'April',5:'May',6:'June',7:'July',8:'August',9:'September',10:'October',11:'November',12:'December'};
            for(let i=0;i<12;i++){
                    if(day <=arr[i]){
                        let month = i+1;
                        date = days_of_year[i]-(arr[i] - day);

                        return info[month] + ', ' + date
                    }
                }
        }

        console.log(getDay(15, false));
        console.log(getDay(41, false));
        console.log(getDay(59, false));
        console.log(getDay(60, false));
        console.log(getDay(366, true));
        console.log(getDay(365, true));
        console.log(getDay(1, true));
        console.log(getDay(112, false)); </script> 
```

<mark>以上为自己思路供大家参考，可能有更优的思路。</mark>

周末愉快