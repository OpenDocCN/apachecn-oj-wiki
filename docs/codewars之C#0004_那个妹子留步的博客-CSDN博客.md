<!--yml
category: codewars
date: 2022-08-13 11:49:09
-->

# codewars之C#0004_那个妹子留步的博客-CSDN博客

> 来源：[https://blog.csdn.net/weixin_41995872/article/details/83387828?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-83387828.nonecase](https://blog.csdn.net/weixin_41995872/article/details/83387828?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-83387828.nonecase)

**你可能知道Facebook和其他网页上的“喜欢”系统。人们可以“喜欢”博客文章，图片或其他项目。我们想要创建应该在这样的项目旁边显示的文本。**

**实现一个函数`likes :: [String] -> String`，它必须包含输入数组，包含喜欢项目的人的名字。它必须返回显示文本，如示例所示：**

```
`Kata.Likes(new string[0]) => "no one likes this"
Kata.Likes(new string[] {"Peter"}) => "Peter likes this"
Kata.Likes(new string[] {"Jacob", "Alex"}) => "Jacob and Alex like this"
Kata.Likes(new string[] {"Max", "John", "Mark"}) => "Max, John and Mark like this"
Kata.Likes(new string[] {"Alex", "Jacob", "Mark", "Max"}) => "Alex, Jacob and 2 others like this"`
```

**`我的`**

```
using System;
using System.Text;
public static class Kata
{
  public static string Likes(string[] name)
  {
     if (name.Length == 0)
        {
            return "no one likes this";
        }
        StringBuilder MyStringBuilder = new StringBuilder(name[0], name.Length + 50);

        if (name.Length==0)
        {
            return "no one likes this";
        }
        else if (name.Length == 1)
        {
            return MyStringBuilder.Append(" likes this").ToString();
        }
        else if (name.Length == 2)
        {
            return MyStringBuilder.Append(" and ").Append(name[1]).Append(" like this").ToString();
            //return name[0] + " and " + name[1] + like;
        }
        else if (name.Length == 3)
        {
            return MyStringBuilder.Append(", ").Append(name[1]).Append(" and ").Append(name[2]).Append(" like this").ToString();
            // return name[0]  +", "+name[1]+" and " + name[2] + like;
        }
        else
        {
            return MyStringBuilder.Append(", ").Append(name[1]).Append(" and ").Append((name.Length - 2).ToString()).Append(" others like this").ToString();
            //return name[0] + ", " + name[1] + " and " + (name.Length-2)+" others " + like;
        }
  }
}
```

其他方法1：

```
public static class Kata
{
  public static string Likes(string[] names)
  {
    switch (names.Length)
    {
      case 0: return "no one likes this"; // :(
      case 1: return $"{names[0]} likes this";
      case 2: return $"{names[0]} and {names[1]} like this";
      case 3: return $"{names[0]}, {names[1]} and {names[2]} like this";
      default: return $"{names[0]}, {names[1]} and {names.Length - 2} others like this";
    }
  }
}
```

其他方法二：

```
using System;

public static class Kata
{
  public static string Likes(string[] name)
  {
    switch (name.Length)
      {
          case 0:
              return "no one likes this";
          case 1:
              return string.Format("{0} likes this",name[0]);
          case 2:
              return string.Format("{0} and {1} like this", name[0], name[1]);
          case 3:
              return string.Format("{0}, {1} and {2} like this", name[0], name[1], name[2]);
          default:
              return string.Format("{0}, {1} and {2} others like this", name[0], name[1], name.Length - 2);
      }
  }
}
```

其他方法四：

```
using System;

public static class Kata
{
  public static string Likes(string[] name)
  {
                return name.Length==0
                ?"no one likes this":name.Length==1?$"{name[0]} likes this"
                :name.Length==2?$"{name[0]} and {name[1]} like this"
                :name.Length==3?$"{name[0]}, {name[1]} and {name[2]} like this"
                :$"{ name[0]}, {name[1]} and {name.Length-2} others like this";
  }
}
```