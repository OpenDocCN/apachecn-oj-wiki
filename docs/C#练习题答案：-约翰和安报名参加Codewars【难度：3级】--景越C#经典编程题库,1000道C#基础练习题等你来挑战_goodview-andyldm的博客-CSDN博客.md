<!--yml
category: codewars
date: 2022-08-13 11:50:45
-->

# C#练习题答案: 约翰和安报名参加Codewars【难度：3级】--景越C#经典编程题库,1000道C#基础练习题等你来挑战_goodview andyldm的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_45444821/article/details/102963807?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-102963807.nonecase](https://blog.csdn.net/weixin_45444821/article/details/102963807?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-102963807.nonecase)

## 约翰和安报名参加Codewars【难度:3级】:

# 答案1:

```
using System;
using System.Collections.Generic;
using System.Linq;

public class Johnann {

    private static List<List<long>> johnAnn(long n) {
        List<long>johnList = new List<long>();
        List<long>annList = new List<long>();
        List<List<long>> res = new List<List<long>>();
        annList.Add(1L);
        johnList.Add(0L);
        if (n == 0) {
            res.Add(annList);
            res.Add(johnList);
        } else {
            long i = 1;
            while (i < n) {
                long j = johnList[(int)(i - 1)];
                long a1 = annList[(int)j];
                johnList.Add(i - a1);
                long a = annList[(int)(i - 1)];
                long j1 = johnList[(int)a];
                annList.Add(i - j1);
                i++;
            }
            res.Add(annList);
            res.Add(johnList);
        }
        return res;
    }
    public static List<long> John(long n) {
        return Johnann.johnAnn(n)[1];
    }
    public static List<long> Ann(long n) {
        return Johnann.johnAnn(n)[0];
    }
    public static long SumJohn(long n) {
        return Johnann.johnAnn(n)[1].Sum();
    }
    public static long SumAnn(long n) {
        return Johnann.johnAnn(n)[0].Sum();
    }
}​ 
```

# 答案2:

```
using System.Collections.Generic;

public class Johnann {

    private static void JohnAnn(long n, ref List<long> listJohn, ref List<long> listAnn)
        {
            listJohn.Add(0);
            listJohn.Add(0);
            listAnn.Add(1);
            listAnn.Add(1);
            for (int i = 2; i < n; i++)
            {
                long tJohn = listJohn[(int)(i - 1)];
                listJohn.Add((int)(i - listAnn[(int)tJohn]));
                long tAnn = listAnn[(int)(i - 1)];
                listAnn.Add((int)(i - listJohn[(int)tAnn]));
            }
        }

        public static List<long> John(long n)
        {
            var listJohn = new List<long>();
            var listAnn = new List<long>();
            JohnAnn(n, ref listJohn, ref listAnn);
            return listJohn;
        }
        public static List<long> Ann(long n)
        {
            var listJohn = new List<long>();
            var listAnn = new List<long>();
            JohnAnn(n, ref listJohn, ref listAnn);
            return listAnn;
        }
        public static long SumJohn(long n)
        {
            var listJohn = John(n);
            long result = 0;
            foreach (var item in listJohn)
                result += item;
            return result;
        }
        public static long SumAnn(long n)
        {
            var listAnn = Ann(n);
            long result = 0;
            foreach (var item in listAnn)
                result += item;
            return result;
        }
}
​ 
```

# 答案3:

```
using System;
using System.Collections.Generic;
using System.Linq;

public class Johnann
{

    public static List<long> John(long n)
    {
        List<long> listJohn = new List<long>();
        List<long> listAnn = new List<long>();
        listJohn.Add(0);
        listAnn.Add(1);
        for (int i = 1; i < n; i++)
        {
            listJohn.Add(i - listAnn[(int)listJohn[i - 1]]);
            listAnn.Add(i - listJohn[(int)listAnn[i - 1]]);
        }
        return listJohn;
    }
    public static List<long> Ann(long n)
    {
        List<long> listJohn = new List<long>();
        List<long> listAnn = new List<long>();
        listJohn.Add(0);
        listAnn.Add(1);
        for (int i = 1; i < n; i++)
        {
            listJohn.Add(i - listAnn[(int)listJohn[i - 1]]);
            listAnn.Add(i - listJohn[(int)listAnn[i - 1]]);
        }
        return listAnn;
    }
    public static long SumJohn(long n)
    {
        return John(n).Sum();
    }
    public static long SumAnn(long n)
    {
        return Ann(n).Sum();
    }

}
​ 
```

# 答案4:

```
using System.Collections.Generic;
using System.Collections;
using System.Linq;
public class Johnann {

    public static List<long> John(long n) {
       return KataCount(n)[1];
    }
    public static List<long> Ann(long n) {
       return KataCount(n)[0];
    }
    public static List<List<long>> KataCount(long n)
    {
       List<long> lstA= new List<long>();
        List<long> lstJ= new List<long>();
        lstA.Add(1);
        lstJ.Add(0);
        for(int indx=1;indx<n;indx++)
        {
        lstJ.Add(indx-lstA[(int)lstJ[indx-1]]);
        lstA.Add(indx-lstJ[(int)lstA[indx-1]]);
        }
        var combinedList= new List<List<long>>();
        combinedList.Add(lstA);
        combinedList.Add(lstJ);

        return combinedList;
    }
    public static long SumJohn(long n) {
       return John(n).Sum(s=>s);
    }
    public static long SumAnn(long n) {
        return Ann(n).Sum(s=>s);
    }
}
​ 
```

# 答案5:

```
using System.Collections.Generic;
using System.Linq;

public class Johnann {

    public static List<long> John(long n)
    {
      List<long> john = new List<long> { 0 };
      List<long> ann = new List<long> { 1 };
      for(int i = 1; i < n; i++)
      {
        john.Add(i - ann[(int)john[i - 1]]);
        ann.Add(i - john[(int)ann[i - 1]]);
      }
      return john;
    }
    public static List<long> Ann(long n)
    {
      List<long> john = new List<long> { 0 };
      List<long> ann = new List<long> { 1 };
      for (int i = 1; i < n; i++)
      {
        john.Add(i - ann[(int)john[i - 1]]);
        ann.Add(i - john[(int)ann[i - 1]]);
      }
      return ann;
    }
    public static long SumJohn(long n)
    {
      return John(n).Sum();
    }
    public static long SumAnn(long n)
    {
      return Ann(n).Sum();
    }
}
​ 
```

# 答案6:

```
using System;
using System.Collections;
using System.Collections.Generic;

public static class DictionaryExtensions
{
    static public List<long> GetList(this Dictionary<long, long> dictionary, long n, Func<long, long> resolve)
    {
        List<long> output = new List<long>();
        for (int i = 0; i < n; i++)
        {
            output.Add(dictionary.GetAt(i, resolve));
        }
        return output;
    }

    static public long GetSum(this Dictionary<long, long> dictionary, long n, Func<long, long> resolve)
    {
        long output = 0;
        for (int i = 0; i < n; i++)
        {
            output += dictionary.GetAt(i, resolve);
        }
        return output;
    }

    static public long GetAt(this Dictionary<long, long> dictionary, long n, Func<long, long> resolve)
    {
        long answer;
        if (dictionary.TryGetValue(n, out answer))
        {
            return answer;
        }
        else
        {
            answer = resolve.Invoke(n);
            dictionary.Add(n, answer);
            return answer;
        }
    }
}

 public static class Johnann
 {
    static private Dictionary<long, long> JohnCache = new Dictionary<long, long>();
    static private Dictionary<long, long> AnnCache = new Dictionary<long, long>();

    static private long john(long n)
    {
      return n.Equals(0) ? 0 : n - AnnCache.GetAt(JohnCache.GetAt(n - 1, john), ann);
    }

    static private long ann(long n)
    {
      return n.Equals(0) ? 1 : n - JohnCache.GetAt(AnnCache.GetAt(n - 1, ann), john);
    }

    public static List<long> John(long n) 
    {
      return JohnCache.GetList(n, john);
    }

    public static List<long> Ann(long n) 
    {
      return AnnCache.GetList(n, ann);
    }

    public static long SumJohn(long n) 
    {
      return JohnCache.GetSum(n, john);
    }

    public static long SumAnn(long n)
    {      
      return AnnCache.GetSum(n, ann);
    }    
}​ 
```

# 答案7:

```
public static TValue GetOrAdd<TKey, TValue>(this IDictionary<TKey, TValue> dictionary, TKey key, Func<TKey, TValue> valueFactory)
{
    TValue val;
    if (!dictionary.TryGetValue(key, out val))
        dictionary.Add(key, val = valueFactory(key));

    return val;
}
​ 
```

# 答案8:

```
using System.Linq;
using System.Collections.Generic;

public class Johnann {

  public static List<long> John(long n) {
    return new Calc(n).John;

  }
  public static List<long> Ann(long n) {
    return new Calc(n).Ann;
  }
  public static long SumJohn(long n) {
    return new Calc(n).John.Sum();

  }
  public static long SumAnn(long n) {
    return new Calc(n).Ann.Sum();
  }
}

public class Calc
{
  public List<long> John=new List<long>();
  public List<long> Ann=new List<long>();

  public Calc(long n)
  {
    John.Add(0);
    Ann.Add(1);
    for (int i = 1; i < n; i++)
    {
      John.Add(i-(int)Ann[(int)John[i-1]]);
      Ann.Add(i-(int)John[(int)Ann[i-1]]);
    }
  }
}​ 
```

# 答案9:

```
using System;
using System.Collections.Generic;
using System.Linq;

public class Johnann
{

  private static List<long>[] 练习题 = new List<long>[] {new List<long> {0}, new List<long> {1}};

  private static long getKata(int ind, long i)
  {
    if (i < 练习题[ind].Count)
    {
      return 练习题[ind][(int)i];
    }
    else
    {
      long kata = i - getKata(1-ind, getKata(ind, i-1));
      练习题[ind].Add(kata);
      return kata;
    }
  }

  private static List<long> getAllKatas(int ind, long n)
  {
    var ls = new List<long>();
    for (long i = 0; i < n; i++) { ls.Add(getKata(ind, i)); }
    return ls;
  }

  public static List<long> John(long n) => getAllKatas(0, n);

  public static List<long> Ann (long n) => getAllKatas(1, n);

  public static long SumJohn(long n) => John(n).Sum();

  public static long SumAnn (long n) => Ann (n).Sum();

}​ 
```

# 答案10:

```
using System.Collections.Generic;
using System.Linq;
public class Johnann {

     static  List<long> john = new List<long>();
      static List<long> ann = new List<long>();
        public static List<long> John(long n)
        {
            john = new List<long>();
            ann = new List<long>();
            for (int i = 0; i < n; i++)
            {
                if (i == 0)
                {
                    john.Add(0);
                    ann.Add(1);
                }
                else
                {
                    john.Add(i - ann[(int)john[(int)i - 1]]);
                    ann.Add(i - john[(int)ann[(int)i - 1]]);                 
                }
            }
            return john;
        }
        public static List<long> Ann(long n)
        {
            John(n);
            return ann;
        }
        public static long SumJohn(long n)
        {
            John(n);
            return john.Sum();
        }
        public static long SumAnn(long n)
        {
            John(n);
            return ann.Sum();
        }
}​ 
```