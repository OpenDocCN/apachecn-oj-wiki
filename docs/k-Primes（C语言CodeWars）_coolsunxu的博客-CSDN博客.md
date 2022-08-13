<!--yml
category: codewars
date: 2022-08-13 11:44:44
-->

# k-Primes（C语言CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105747827?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-105747827.nonecase](https://blog.csdn.net/coolsunxu/article/details/105747827?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-105747827.nonecase)

解题思路：

（1）首先求出因数的个数，并同时插入链表

（2）接下来，用开始的函数分别求出1,3,7的链表

（3）三层循环，判断个数，有点百钱买鸡的味道

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// In the preloaded section are some functions that can help.
// They can be used as a small library.
// There is no file to include, only the templates below.

struct node {
    int data;
    struct node *next;
};
struct list {
    size_t sz;
    struct node *head;
};

struct list* createList();

// push data at the head of the list
void insertFirst(struct list* l, int data);

struct list* reverse(struct list* l);

void listFree(struct list* l);

// functions to write
struct list* kPrimes(int k, int start, int nd) {
    // your code
    struct list* l = createList();
    for(int i=start;i<=nd;i++) {
      if(kprime(i)==k) insertFirst(l, i);
    }
    struct list* lr = reverse(l);
    //listFree(l);
    return lr;
}
int puzzle(int s) {
    // your code
    struct list* l1 = kPrimes(1, 2, s);
    struct list* l3 = kPrimes(3, 2, s);
    struct list* l7 = kPrimes(7, 2, s);
    struct node *p=l1->head,*q=l3->head,*h=l7->head;
    int sum = 0,count=0;
    while(p) {
    sum = p->data;
    q = l3->head;
    while(q) {
      sum = p->data+q->data;
      h = l7->head;
      while(h) {
        if(sum+h->data<s) h = h->next;
        else if(sum+h->data==s) {
          count++;
          break;
        } else break;
      }
      q = q->next;
    }
    p = p->next;
  }
  return count;
}

int kprime(int n) {
  if (n==1) return 1;
  int i=2,count=0;
  while(n>1 && i<=n) {
    if(n%i==0) n/=i,count++;
    else i++;
  }
  return count;
}
```