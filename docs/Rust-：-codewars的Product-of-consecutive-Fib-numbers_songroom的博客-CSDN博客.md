<!--yml
category: codewars
date: 2022-08-13 11:48:03
-->

# Rust : codewars的Product of consecutive Fib numbers_songroom的博客-CSDN博客

> 来源：[https://blog.csdn.net/wowotuo/article/details/78147766?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-78147766.nonecase](https://blog.csdn.net/wowotuo/article/details/78147766?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-78147766.nonecase)

The Fibonacci numbers ：Fn:
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, …
其中关系式有：
F(n) = F(n-1) + F(n-2) with F(0) = 0 and F(1) = 1.

给定一个数，请试图找出其是否可以由其中的连续相邻The Fibonacci numbers相乘而得；
如果不能相乘而得，请找出其上边界值。写出productFib函数。举例：

productFib(714) # should return (21, 34, true),
# since F(8) = 21, F(9) = 34 and 714 = 21 * 34

productFib(800) # should return (34, 55, false), =>上边界值
# since F(8) = 21, F(9) = 34, F(10) = 55 and 21 * 34 < 800 < 34 * 55

一、我的解法

```
fn product_fib(prod: u64) -> (u64, u64, bool) {

    let mut hp: HashMap<u64, u64> = HashMap::new();
    hp.insert(1u64, 0u64);
    hp.insert(2u64, 1u64);
    hp.insert(3u64, 1u64);
    let mut vec: Vec<u64> = Vec::new();
    vec.push(0u64);
    vec.push(1u64);
    vec.push(1u64);
    let mut result: Vec<u64> = Vec::new();
    for i in 3u64.. {
        let i_1 = hp.get(&(i - 1)).unwrap().clone();
        let i_2 = hp.get(&(i - 2)).unwrap().clone();
        let val = i_2 + i_1;
        hp.insert(i, val);
        vec.push(val);
        let val_i_2 = &vec[(i - 2) as usize];
        let val_i_1 = &vec[(i - 1) as usize];
        let val_i = &vec[i as usize];

        if val_i_1 * val_i == prod||
        (val_i_2 * val_i_1 < prod, val_i_1 * val_i > prod) == (true, true) {
            result.push(*val_i);
            result.push(*val_i_1);
            break;
        }
    }
    (*result.get(0).unwrap(),
     *result.get(1).unwrap(),
     prod == *result.get(0).unwrap() * *result.get(1).unwrap())
} 
```

二、精彩的解法

1、

```
fn product_fib(prod: u64) -> (u64, u64, bool) {
    let mut a = 0; let mut b = 1;
    while a * b < prod {
        let tmp = a;
        a = b;
        b = tmp + b;
    } 
    let bl = if a * b == prod {true} else {false};
    (a, b, bl)
}
```

2、

```
use std::cmp::Ordering::{Greater, Equal};
fn product_fib(prod: u64) -> (u64, u64, bool) {
  let mut p0 = 0;
  let mut p1 = 1;
  loop {
    let p = p0 * p1;
    match p.cmp(&prod) {
      Greater => return (p0, p1, false),
      Equal => return (p0, p1, true),
      _ => ()
    };
    let p2 = p0 + p1;
    p0 = p1;
    p1 = p2;
  }
}
```

3、

```
fn product_fib(prod: u64) -> (u64, u64, bool) {
    let mut f = (0, 1);
    loop {
        f = (f.1, f.0 + f.1);
        if f.0 * f.1 >= prod {
            return (f.0, f.1, f.0 * f.1 == prod);
        }
    }
}
```

4、

```
use std::cmp::Ordering;

fn product_fib(prod: u64) -> (u64, u64, bool) {
    let mut fib_vec: Vec<u64> = vec![0,1];
    let mut v_len = fib_vec.len();
    loop {
        let (n, n_1) = (fib_vec[v_len-1], fib_vec[v_len-2]);
        match (n*n_1).cmp(&prod) {
            Ordering::Less => {
                let next_fib = n + n_1;
                fib_vec.push(next_fib);
                v_len = fib_vec.len();
            },
            Ordering::Equal => { return (n_1, n, true); },
            Ordering::Greater => { return (n_1, n, false); },
        }
    }
}
```