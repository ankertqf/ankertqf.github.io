---
title: Hexo 文章多级分类
date: 2020-03-19 11:33:56
categories: 
- hexo
tags: 
- 多级分类
---

# Hexo 文章多级分类
Hexo原生支持父子分类，只需要在 Front-matter中的分类标记后面写下多个分类就行了。写在后面的分类就在前面分类的子分类，例如：

```
categories: 
- Matlab
- Matlab知识点
```
会使分类**Matlab知识点**成为**Matlab**的子分类，而不是并列分类。