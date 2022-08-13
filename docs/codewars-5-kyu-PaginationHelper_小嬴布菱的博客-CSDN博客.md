<!--yml
category: codewars
date: 2022-08-13 11:29:20
-->

# codewars 5 kyu PaginationHelper_小嬴布菱的博客-CSDN博客

> 来源：[https://blog.csdn.net/qq_29549685/article/details/117691942?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-117691942.142^v40^control,185^v2^control](https://blog.csdn.net/qq_29549685/article/details/117691942?ops_request_misc=&request_id=&biz_id=102&utm_term=codewars&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-8-117691942.142^v40^control,185^v2^control)

### 我的题解

构造函数并完成方法。

```
 function PaginationHelper(collection, itemsPerPage) {
  this.collection = collection;
  this.itemsPerPage = itemsPerPage;
}

PaginationHelper.prototype.itemCount = function () {
  return this.collection.length;
};

PaginationHelper.prototype.pageCount = function () {
  return Math.ceil(this.collection.length / this.itemsPerPage);
};

PaginationHelper.prototype.pageItemCount = function (pageIndex) {

  if (pageIndex > this.pageCount() - 1) {
    return -1;
  } else if (pageIndex == this.pageCount() - 1) {
    return this.collection.length % this.itemsPerPage;
  } else {
    return this.itemsPerPage;
  }
};

PaginationHelper.prototype.pageIndex = function (itemIndex) {
  if (!this.collection.length) {
    return -1;
  } else if (itemIndex > this.collection.length || itemIndex < 0) {
    return -1;
  } else {
    return Math.floor(itemIndex / this.itemsPerPage);
  }
}; 
```

### 优秀题解

```
class PaginationHelper {
  constructor(a, p) {
    Object.assign(this, { a, p });
  }
  itemCount() {
    return this.a.length;
  }
  pageCount() {
    return -~(this.a.length / this.p);
  }
  pageItemCount(i) {
    return i < this.pageCount()
      ? (i + 1) * this.p <= this.itemCount()
        ? this.p
        : this.itemCount() % this.p
      : -1;
  }
  pageIndex(i) {
    return i < 0 || i >= this.itemCount() ? -1 : (i / this.p) | 0;
  }
} 
```

```
function PaginationHelper(collection, itemsPerPage) {
  this.collection = collection, this.len = this.collection.length, this.ipp = itemsPerPage;
}
PaginationHelper.prototype.itemCount = function() {return this.len;}
PaginationHelper.prototype.pageCount = function() {return Math.ceil(this.len / this.ipp);}
PaginationHelper.prototype.pageItemCount = function(pageIndex) {
  var pc = this.pageCount();
  return pc <= pageIndex || pageIndex < 0 ? -1 : pc - 1 == pageIndex ? this.len % this.ipp : this.ipp;
}
PaginationHelper.prototype.pageIndex = function(itemIndex) {
  return this.len <= itemIndex || itemIndex < 0 ? -1 : Math.floor(itemIndex / this.ipp); 
```

### 总结

学到了 JS 的函数写法，以及函数的声明、调用。