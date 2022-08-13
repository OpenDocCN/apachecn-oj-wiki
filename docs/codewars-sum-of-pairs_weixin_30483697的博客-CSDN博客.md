<!--yml
category: codewars
date: 2022-08-13 11:38:45
-->

# codewars sum of pairs_weixin_30483697的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_30483697/article/details/97481985?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-6-97481985-null-null.142^v40^control,185^v2^control&utm_term=codewars](https://blog.csdn.net/weixin_30483697/article/details/97481985?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166036058916781685355945%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=166036058916781685355945&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-6-97481985-null-null.142^v40^control,185^v2^control&utm_term=codewars)

## Sum of Pairs

Given a list of integers and a single sum value, return the first two values (parse from the left please) in order of appearance that add up to form the sum.

```
sum_pairs([11, 3, 7, 5],         10) 
```

Negative numbers and duplicate numbers can and will appear.

**NOTE: There will also be lists tested of lengths upwards of 10,000,000 elements. Be sure your code doesn't time out.**

这道题目的意思是说：给出一个数组，然后给出一个number，需要从数组中找到两个元素的和等于目标值得number，如果有多对组合的，需要对多对组合进行下标比对，下标整体靠前的就是目标选项，将该组合返回即可，如果没有找到，返回undefined。

特别注意的是，它的测试中会有一个特别长的数组，长度可能会超过10,000,000个元素，如果你的算法不够高效，很有可能会超时，它设置的超时时间是12s。

我思考了半天，第一个办法是按照常规，双重for循环找到所有组合，然后再对找到的所有组合比对下标，整体靠前的返回。

没错，你想到了，方法没错，返回超时。

方法二：这回学聪明了，先找到一组组合，然后再循环时从比它下标小的范围内寻找，如果没有找到，就把第一组组合返回，如果找到了就替换，然后继续在更小的范围内寻找。最坏的情况是都找完，找不到的话，返回undefined。

以为优化了不少了，但是依然timeout。

```
/your code here
      let result = [];
      let pos = 0; for (let i = 0; i < ints.length - 1; i++) { if (result[1]) { if(i>pos){ break;
          } for (let j = i + 1; j < pos; j++) { if (ints[i] + ints[j] == s) {
                result = [ints[i], ints[j]];
            }
          }
        } else { for (let j = i + 1; j < ints.length; j++) { if (ints[i] + ints[j] == s) { if (!result[1] || (result[1] && result[1] > j)) {
                result = [ints[i], ints[j]];
                pos = j;
              }
            }
          }
        }
      } return result.length > 0 ? result : undefined;
```

没错，我就是这么菜，水平到这里了，江郎才尽了。。。

不过别失望，带你去看看大神的代码吧，吸收一点经验也是好的。

大神代码：

```
var sum_pairs=function(ints, s){ var seen = {} for (var i = 0; i < ints.length; ++i) { if (seen[s - ints[i]]) return [s - ints[i], ints[i]];
    seen[ints[i]] = true }
}
```

什么，代码居然可以这么简练？没错，就是这么简练，然后细细品味一番，它巧妙的把对比过的数字变成一个对象的属性并且设置为true，然后用seen(s-ints[i])是否为true来判定是否找到了组合，一旦找到了，它们的下标必定是最小的。因为该方法的重点就是找到最小的下标值，控制好了最小下标值，你就赢了！！！