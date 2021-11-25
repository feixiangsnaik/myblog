---
title: less
date: 2021-11-25 11:05:02
tags:
---
## 1.混入
样式混入可以使用混入的方式。
```
.common-titile{
  color:red;
}
.title{
  .common-titile;
  font-size:20px;
}
```