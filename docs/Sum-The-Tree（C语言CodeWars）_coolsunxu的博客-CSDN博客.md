<!--yml
category: codewars
date: 2022-08-13 11:51:31
-->

# Sum The Tree（C语言CodeWars）_coolsunxu的博客-CSDN博客

> 来源：[https://blog.csdn.net/coolsunxu/article/details/105874468?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-105874468.nonecase](https://blog.csdn.net/coolsunxu/article/details/105874468?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-105874468.nonecase)

解题思路：

（1）递归求解，采用哪种遍历方式都可以

```
typedef struct node {
  int value;
  struct node* left;
  struct node* right;
}Node;

void preorder(Node* root,int *sum) {
  if(root) {
    *sum = *sum + root->value;
    preorder(root->left,sum);
    preorder(root->right,sum);
  }
  return;
}

int sumTheTreeValues(Node* root) {
  int sum = 0;
  preorder(root,&sum);
  return sum;
}
```

（2）测试程序CodeWars

```
#include <criterion/criterion.h>
#include <stdlib.h> // rand(), malloc(), free()
#include <stddef.h> // NULL

struct node
{
  int value;
  struct node* left;
  struct node* right;
};

void build_tree(struct node* current, int sum)
{
  if (sum > 0) current->value = rand()%sum + 1;
  else current->value = 0;
  sum -= current->value;

  if (sum > 0) {
    int part = rand()%16 + 1;
    current->left = (struct node*)malloc(sizeof(struct node));
    current->right = (struct node*)malloc(sizeof(struct node));

    build_tree(current->left, sum/part);
    build_tree(current->right, sum - sum/part);
  }
  else {
    current->left = current->right = NULL;
  }
}

void remove_tree(struct node* current)
{
  if (current == NULL) return;

  remove_tree(current->left);
  remove_tree(current->right);
  free(current);
}

int sumTheTreeValues(struct node*);

void dotest(int expected)
{
  struct node* root = (struct node*)malloc(sizeof(struct node));
  int actual = 0;

  build_tree(root, expected);

  actual = sumTheTreeValues(root);

  if (root != NULL) remove_tree(root);
  root = NULL;

  cr_assert_eq(expected, actual, "Expected %d, but got %d.\n", expected, actual);
}

Test(the_multiply_function, should_pass_all_the_tests_provided)
{
  dotest(4);
  dotest(8);
  dotest(15);
  dotest(16);
  dotest(23);
  dotest(42);
}
```