---
layout: post
title: a post with code
date: 2023-11-09 20:09:00
description: OpenMP running time and stack size for threads
tags: formatting code
categories: coding
featured: true
---

# OpenMP的堆栈问题

今天在写代码的时候遇到一个很奇怪的问题，一套相同的函数，对少量数据可以通过OpenMP并行计算，但是对比较大的数据，intel fortran编译的库直接返回segmentation fault core dumped。

这个很奇怪啊，因为在编译链接的时候已经设置了heapsize，后面查阅资料发现，使用OpenMP并行的时候需要指定其他线程的StackSize，于是添加环境变量，

```shell
echo "ulimit -s unlimit" > ~/.zshrc
source ~/.zshrc
```



