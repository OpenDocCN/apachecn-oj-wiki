<!--yml
category: codewars
date: 2022-08-13 11:46:21
-->

# codewars解题笔记---DNA to RNA Conversion_cxc_happy111的博客-CSDN博客

> 来源：[https://blog.csdn.net/cxc_happy111/article/details/86541280?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-86541280.nonecase](https://blog.csdn.net/cxc_happy111/article/details/86541280?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-5-86541280.nonecase)

原题：

Deoxyribonucleic acid, DNA is the primary information storage molecule in biological systems. It is composed of four nucleic acid bases Guanine ('G'), Cytosine ('C'), Adenine ('A'), and Thymine ('T').

Ribonucleic acid, RNA, is the primary messenger molecule in cells. RNA differs slightly from DNA its chemical structure and contains no Thymine. In RNA Thymine is replaced by another nucleic acid Uracil ('U').

Create a funciton which translates a given DNA string into RNA.

For example:

```
new Bio().dnaToRna("GCAT") // returns "GCAU" 
```

The input string can be of arbitrary length - in particular, it may be empty. All input is guaranteed to be valid, i.e. each input string will only ever consist of `'G'`, `'C'`, `'A'` and/or `'T'`.

Sample Tests:

```
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class BioTest {
    @Test
    public void testDna() throws Exception {
        Bio b = new Bio();
        assertEquals("UUUU", b.dnaToRna("TTTT"));
    }

    @Test
    public void testDna2() throws Exception {
        Bio b = new Bio();
        assertEquals("GCAU", b.dnaToRna("GCAT"));
    }
}
```

Solution: 

```
public class Bio {
    public String dnaToRna(String dna) 
        return dna;  // Do your magic!
    } 
}
```

解释说明：

题目：脱氧核糖核酸是生物系统中主要的信息存储分子。由四种核酸碱基鸟嘌呤（G’）、胞嘧啶（C’）、腺嘌呤（A’）和胸腺嘧啶（T’）组成。

核糖核酸是细胞中的主要信使分子。RNA与DNA的化学结构稍有不同，不含胸腺嘧啶。在RNA中，胸腺嘧啶被另一种核酸尿嘧啶（“U”）取代。

创建一个功能，将给定的DNA字符串转换成RNA。

例如：

```
new Bio().dnaToRna("GCAT") // returns "GCAU"
```

输入字符串可以是任意长度，尤其是可以是空的。所有输入均保证有效，即每个输入字符串仅由“g”、“c”、“a”和/或“t”组成。

我的答案：

```
public class Bio {
    public String dnaToRna(String dna) {
        dna = dna.replace("T","U");//把T替换成U
        return dna;  // Do your magic!
    } 
}
```